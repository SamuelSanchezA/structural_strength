/*
Name: Samuel Sanchez
Team: Athena Raya, Evelyn Murillo, Regie Daquioag 
Date: 2 November 2015
Description: Determines the variance and standard deviation of a set of values

According to the addition of 3 times the standard deviation to the breaking point of 16000 Newtons is 19572.31 Newtons for steel and 18837.634 Newtons for graphite. For steel, 2/10 coupons passed. For graphite, 6/10 coupons passed. With a 20% passing rate for the steel coupons and a 60% passing rate for the graphite coupons, neither prove to be successful and need to be increased to a safety factor of s = 3 in order to produce a higher safety rating.
*/

#include <iostream> // cin, cout 
#include <cstdlib> // exit(1)
#include <fstream> // ifstream, ofstream, open(), close()
#include <iomanip> // setw()
#include <cmath> // pow(), sqrt()
#include <vector> // size()

using namespace std;
//******************************************************************************** 
double mean(vector<int> v, int n);
// Summary: Calculates the mean of the vector indexed values and returns them to other functions
// Precondition: Needs a vector and the element count 
// Postcondition: Returns the mean
//********************************************************************************
void minimumVec(vector<int> vec, int n);
// Summary: Caluclates the minimum idexed value
// Precondition: Needs a vector and the element number
// Postcondition: Prints the minimum value
//********************************************************************************
void maximumVec(vector<int> vec, int n);
// Summary: Calculates the maximum indexed value
// Precondition: Needs a vector and an element
// Postcondition: Prints out the max
//********************************************************************************
void variance(vector<int> v, int n);
//Summary: Determines the variance of a list of numbers
//Precondition: Needs a vector along with the number of elements
//Postcondition: Prints out the variance
//********************************************************************************
void standardDev(vector<int> v, int n);
//Summary: Determines the standard deviation of a list of numbers
//Precondition: Needs a vector and a the number of elements in the vector
//Postcondition: Prints out standard deviation
//********************************************************************************

int main()
{
    int iterator;
    ifstream fin1, fin2;
    vector<int> steel; // One vector for steel and another for graphite results
    vector<int> graphite;
    int element1 = 0, element2 = 0; // Keeps track of the number of values in each data text 
    fin1.open("data1.txt"); // Steel data
    fin2.open("data2.txt"); // Graphite data
    
    if(fin1.fail() || fin2.fail())
    {
        cout << "Error on opening files" << endl;
        exit(1);
    }
    
    while(fin1 >> iterator) // Steel data fills indices of vector steel
    {
        steel.push_back(element1);
        steel[element1] = iterator;
        element1++;
    }
    
    while(fin2 >> iterator)
    {
        graphite.push_back(element2); // Data fills indices of vector graphite
        graphite[element2] = iterator;
        element2++;
    }
    
    cout << "Mean: "<< mean(steel, element1) << " Newtons" << endl;
    maximumVec(steel, element1);
    minimumVec(steel, element1);
    variance(steel, element1);
    standardDev(steel, element1);
    cout << endl;

    cout << "Mean: "<< mean(graphite, element2) << " Newtons" << endl;
    maximumVec(graphite, element2);
    minimumVec(graphite, element2);    
    variance(graphite, element2);
    standardDev(graphite, element1);
    
    fin1.close(); // Input files closed
    fin2.close();
    return 0;
}

double mean(vector<int> v, int n) // Will be called in stdDev() and Variance()
{
    double mean;
    double sum = 0;
    for(int xi = 0; xi < n; xi++)
    {
        sum += v[xi]; // Adds values
    }
    mean = sum / n; // Divides values by number of values
    return mean;
}

void maximumVec(vector<int> vec, int n)
{
    int max = vec[0]; // Set to first value
    for(int ix = 1; ix < n; ix++)
    {
        if(vec[ix] > max)
        {
            max = vec[ix]; //Sifts through values to find highest value
        }
    }
    cout << "Maximum Coupon: " << max << " Newtons"<<  endl;
    return;
}

void minimumVec(vector<int> vec, int n)
{
    int min = vec[0]; // Set to first value
    for(int ix = 1; ix < n; ix++)
    {
        if(vec[ix] < min)
        {
            min = vec[ix]; // Sifts through numbers to find lowest value
        }
    }
    cout << "Minimum Coupon: " << min << " Newtons"<< endl;
    return;
}

void variance(vector<int> v, int n)
{
    double sum = 0;
    double meanVal = mean(v, n); 
    double variance;
   
    for(int xi = 0; xi < n; xi++)
    {
        sum +=  pow((v[xi] - meanVal), 2); // Each value is subtracted by the mean and raised to the power of two, then are added together 
    }
    variance = (sum/n); // Sum is then divided by number of values
    cout << "Variance: " << variance << " Newtons"<< endl;
    return;
}

void standardDev(vector<int> v, int n)
{
    int sum = 0;
    double meanVal = mean(v, n);
    double stdDev;
    
    for(int xi = 0; xi < n; xi++)
    {
        sum +=  pow((v[xi] - meanVal), 2); 
    }
    stdDev = sqrt(sum/n); // Same as variance, except square root of variance is being taken
    cout << "Standard Deviation: "<< stdDev << " Newtons" << endl;
    return;
}
