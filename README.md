CheeseProblem
=============

Forgive me for not implementing github correctly and putting all of this in the README, I'm not familiar with github. This program is supposed to take the length, width and height of a block of swiss cheese and then calculating the volume after subtracting the bubbles and cylinders of empty space inside the cheese. 

=============
//Homework 5 Swiss Cheese
//Section 001
//
//Description: calculate the volume of the swiss cheese.
//Inputs: length, width, height, radius of sphere, radius of cylinder, height of cylinder, and number of holes of each kind.
//Outputs: final volume of swiss cheese.
//Processing: total volume - volume of spherical holes - volume of cylindrical holes.
 
#include <iostream>
#include <string>
using namespace std;
 
const double pi = 3.14159;
 
void dimensionConfirm(double&, string);
void holesConfirm(int&, string);
double cheeseVolume(double, double, double);
double sphereVolume(double, double);
double cylinderVolume(double, double, double);
double finalVolume(double, double, double, int, double, int, double, double);
 
int main()
{
	double height=0, length=0, width=0, volume=0, sphrad=0, cylrad=0, cylheight=0;
	int sphnum=0, cylnum=0;
 
	cout<<"Enter the length of the hunk of cheese:"<<endl;
	cin>>length;
	dimensionConfirm(length, "length");
 
	cout<<"Enter the width:"<<endl;
	cin>>width;
	dimensionConfirm(width, "width");
 
	cout<<"Enter the height:"<<endl;
	cin>>height;
	dimensionConfirm(height, "height");
 
 
	cout<<"Enter the number of spherical bubbles:"<<endl;
	cin>>sphnum;
	holesConfirm(sphnum, "number of spherical bubbles");
 
	if (sphnum>0){
	cout<<"Enter in the radius of the spherical bubbles:"<<endl;
	cin>>sphrad;
	dimensionConfirm(sphrad, "spherical bubble radius");
	}
 
	cout<<"Enter the number of surface cylinders:"<<endl;
	cin>>cylnum;
	holesConfirm(cylnum, "number of surface cylinders");
 
	if (cylnum>0){
	cout<<"Enter in the radius of the surface cylinders:"<<endl;
	cin>>cylrad;
	dimensionConfirm(cylrad, "surface cylinder radius");
 
	cout<<"Enter in the height of the surface cylinders:"<<endl;
	cin>>cylheight;
	dimensionConfirm(cylheight, "height of the surface cylinders:");
 
	}
 
	volume = finalVolume(length, width, height, sphnum, sphrad, cylnum, cylrad, cylheight);
	cout<<"The total volume of cheese present is "<<volume<<" cubic centimeters."<<endl;
}
 
void dimensionConfirm(double& a, string b)
{
		if(a<=0){
			cout<<b<<" must be greater than 0. Enter in the "<<b<<endl;
			cin>>a;
		}else{
			return &a;
		}
}
 
void holesConfirm(int& a, string b)
{
		while(a<0){
		cout<<b<<" must be greater or equal to 0. Enter in the "<<b<<endl;
		cin>>a;
		}
}
 
double cheeseVolume(double l, double w, double h){
	return (l*w*h);
}
 
double sphereVolume(double pi, double r){
	return ((4/3)*pi*(r*r*r));
}
 
double cylinderVolume(double pi, double r, double h){
	return (pi*(r*r)*h);
}
 
double finalVolume(double length, double width, double height, int sphnum, double sphrad, int cylnum, double cylrad, double cylheight){
	double volume = cheeseVolume(length, width, height);
	if (sphnum>0 && cylnum>0)
		volume = volume - (sphnum*(sphereVolume(pi, sphrad))) - (cylnum*(cylinderVolume(pi, cylrad, cylheight)));
	return volume;
}
