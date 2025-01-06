
// **    INTRODUCTION:-   **

/*....THIS IS A PROJECT ON E-COMMERCE INVENTORY MANAGEMENT SYSTEM PUT FORWARD BY 3RD SEM C DIV OF KLE TECH CS PEERS/STUDENTS
  BY IMPLEMENTING DATA STRUCTURE AND ALGORITHMS CONCEPT INTO THIS PROJECT USING C++ PROGRAMMING LANGUAGE, WHERE BASIC TO ADVANCE LEVELED CONCEPTS ARE
  USED HERE.THIS PROJECT INCLUDES VARIOUS SECTION TO UNSERSTAND AND GO TO EACH SECTION FLEXIBILY WE HAVE ADDED
  COMMENT AND PARTITION  HAS BEEN MADE AND TO ATTRACT THE USER WE HAVE USED COLOURS IT ACTUALLY GIVES THE FEEL OF REALTIME
  SIMULATION OF INVENTORY......


  //   ***  ABOUT THE PROJECT   ***
     GOING INTO THE PROJECT THE AS WE KNOW THE PROJECT STARTS WITH HAEDER SECTION
     NEXT COMES THE ADDITIONAL ATTRIBUTES USAGES FOR ADDING COLOURS, INCREASE THE DYNAMIC NATURE.
     MOVING FURTHER FUNCTIONS , STRUCTURES ,ARRAYS , HASH TABLE AND VECTORS AND DIFFERENT SORTING METHODS,SEARCHING ARE IMPLEMENTED ALONG WITH THAT
     CONDITIONAL,BREAK AND CONTINUE STATEMENTS ARE ALSO....

     THANK-YOU FOR YOUR TIME
                               ITS TIME TO EXPLORE ...............................



   */


//SECTION 1:-   HEADERS SECTION.
#include <iostream>
#include <windows.h>
#include <string>
#include <thread>
#include <chrono>
#include <cstdlib>  // For system("CLS")
#include <fstream>
#include <sstream>  // for std::stringstream
#include <limits>   // for std::numeric_limits
#include<algorithm>
#include<vector>
#include <map>
#include <set>  // Add this line to use std::set
#include <unistd.h> // For sleep function in Unix-based systems
#include <iomanip>
#include <ctime>    // For working with dates
#include <stdexcept>
#include <unordered_map>
#include<conio.h>
//------------------------------------------------------------------------

// ATTRIBUTS TO ADD COLOURS AND MAKING IT DYNAMIC.
#define RESET   "\033[0m"
#define RED     "\033[31m"
#define GREEN   "\033[32m"
#define YELLOW  "\033[33m"
#define BLUE    "\033[34m"
using namespace std;

//------------------------------------------------------------------------

//SECTION 2:

// THIS FUNCTION PART WILL BE USED IN PROGRAM TO GET THE TIME AND DATE RELATED TO ECOMMERCE DATASET PRESENT IN CSV FILE.

string getCurrentDate()
{
    time_t now = time(0);
    tm *ltm = localtime(&now);
    // Format the date as "YYYY-MM-DD"
    char buffer[11];
    strftime(buffer, sizeof(buffer), "%Y-%m-%d", ltm);
    return std::string(buffer);
}

//------------------------------------------------------------------------


// Function to simulate a delay effect

void delayPrint(const string& text, int delayMs)
{
    for (char c : text) {
        cout << c << flush;
        this_thread::sleep_for(chrono::milliseconds(delayMs));
    }
    cout << endl;
}

//------------------------------------------------------------------------

// Function to clear the screen (works on both Windows and Linux/macOS)

void clearScreen()
{
    #if defined(_WIN32)
        system("CLS");  // For Windows
    #else
        system("clear");  // For Linux/Mac
    #endif
}

//------------------------------------------------------------------------

// Color settings for Windows
void setColor(int colorCode)
{
    #if defined(_WIN32)
        system(("color " + to_string(colorCode)).c_str());
    #else
        // ANSI escape codes for Linux/Mac
        if (colorCode == 1) cout << "\033[31m"; // Red
        else if (colorCode == 2) cout << "\033[32m"; // Green
        else if (colorCode == 3) cout << "\033[33m"; // Yellow
        else if (colorCode == 4) cout << "\033[34m"; // Blue
        else if (colorCode == 5) cout << "\033[35m"; // Magenta
        else if (colorCode == 6) cout << "\033[36m"; // Cyan
        else cout << "\033[0m"; // Reset
    #endif
}


//------------------------------------------------------------------------


// Function to display an e-commerce related ASCII art image (Shopping Cart)

void displayImage()
{
    string shoppingCartArt = R"(
     ________
    /        \
   /__PRODUCT_\
   |  ______  |
   | |      | |
   | |      | |
   | |_E-COM| |
   |__________|
      |    |
      |    |
    __|____|__
   |__PLATFORM|
    )";
    delayPrint(shoppingCartArt, 10);
}

//------------------------------------------------------------------------


// Function to set console text color
void SetConsoleColor(int color)
{

    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), color);
}
//------------------------------------------------------------------------

// Function to display the banner

void displayBanner()
{
    SetConsoleColor(10);  // Light Green
    std::cout << "\n\n";
    std::cout << "###############################################################\n";
    std::cout << "#                                                             #\n";
    std::cout << "#             WELCOME TO THE E-COMMERCE INVENTORY SYSTEM      #\n";
    std::cout << "#                                                             #\n";
    std::cout << "###############################################################\n\n";
     // Delay to keep banner visible
}

//------------------------------------------------------------------------

// Function to display an animated front cover page

void displayFrontPage()
{
    clearScreen(); // Clear the console screen before displaying the front page

    // Set title color
    setColor(2);  // Green
    delayPrint("*****************************************", 50);
    delayPrint("*                                       *", 75);

    // Display animated title
    setColor(4);  // Blue
    delayPrint("*   E-Commerce Inventory Management       *", 100);
    setColor(3);  // Yellow
    delayPrint("*                                         *", 75);
    delayPrint("*  Welcome to the ultimate product        *", 75);
    delayPrint("*  management system for your E-commerce  *", 75);
    delayPrint("*  business! Easily manage your inventory *", 75);
    delayPrint("*  with just a few clicks.                *", 75);
    delayPrint("*                                         *", 50);
    delayPrint("*****************************************", 50);

    cout << "\n\n";

    // Simulate loading effect with dynamic colors
    setColor(6);  // Cyan
    delayPrint("Loading System...", 100);
    this_thread::sleep_for(chrono::seconds(2)); // 2 seconds delay
    delayPrint("Please wait...", 100);
    this_thread::sleep_for(chrono::seconds(2)); // 2 seconds delay
    cout << "\n";

    delayPrint("Press Enter to continue...", 100);
    cin.get();  // Wait for user input (pressing Enter)

    // Display an e-commerce related ASCII image (Shopping Cart)
    setColor(5);  // Magenta
    displayImage();
    setColor(0);  // Reset color to default
}

//------------------------------------------------------------------------

// Function to display system description

void displayDescription()
{
    SetConsoleColor(14);  // Yellow
    std::cout << "This is your one-stop solution to manage inventory for your\n";
    std::cout << "E-commerce platform. With this system, you can easily track\n";
    std::cout << "products, update stock, manage orders, and maintain a smooth\n";
    std::cout << "flow of goods in your online store.\n\n";
    this_thread::sleep_for(chrono::seconds(1)); // Delay to keep the description visible
}

//------------------------------------------------------------------------

// Function to display the features

void displayFeatures()
{
    SetConsoleColor(11);  // Light Blue
    std::cout << "Key Features:\n";
    SetConsoleColor(7);   // White
    std::cout << "- Add, update, and remove products\n";
    std::cout << "- Track product stock in real-time\n";
    std::cout << "- Manage product categories\n";
    std::cout << "- View detailed product reports\n";
    std::cout << "- Order management system\n";
    std::cout << "- Customizable settings for advanced users\n\n";
    this_thread::sleep_for(chrono::seconds(3)); // Delay to keep the features visible
}

//------------------------------------------------------------------------

// Function to display instructions

void displayInstructions()
{
    SetConsoleColor(13);  // Light Purple
    std::cout << "Instructions to Navigate the System:\n";
    SetConsoleColor(7);   // White
    std::cout << "1. To add products, select '1' from the main menu.\n";
    std::cout << "2. To update stock, select '2'.\n";
    std::cout << "3. To view product reports, select '3'.\n";
    std::cout << "4. To manage orders, select '4'.\n";
    std::cout << "5. To exit the system, select '0'.\n";
    std::cout << "You can enter your choice by typing the number and pressing Enter.\n\n";
    this_thread::sleep_for(chrono::seconds(3)); // Delay to keep instructions visible
}

//------------------------------------------------------------------------

// Footer Function

void displayFooter()
{
    SetConsoleColor(15);  // White
    std::cout << "###############################################################\n";
    std::cout << "#                                                             #\n";
    std::cout << "#          Developed by SOURAV   -  CS major of  KLE TECH     #\n";
    std::cout << "#                                                             #\n";
    std::cout << "###############################################################\n";
}


//==========================================================================
//TILL THIS IT WAS ALL ABOUT FEONT PAGE BUT FROM HERE THE FUNCTIONS ARE USED TO DO OPERATIONS BASED ON USER REQUEST.


//------------------------------------------------------------------------

// Function to print text in different colors

void printColor(const string &text, const string &color)
{
    string colorCode;
    if (color == "red") colorCode = "\033[1;31m"; // Red
    else if (color == "green") colorCode = "\033[1;32m"; // Green
    else if (color == "yellow") colorCode = "\033[1;33m"; // Yellow
    else if (color == "blue") colorCode = "\033[1;34m"; // Blue
    else if (color == "reset") colorCode = "\033[0m"; // Reset color

    cout << colorCode << text << "\033[0m";
}

//------------------------------------------------------------------------

// Simple login function to simulate a login page


bool login()
{
    string username, password;
    const string correctUsername = "admin";  // Example username
    const string correctPassword = "admin123";  // Example password

    printColor("\n=== Login Page ===\n", "green");
    printColor("Please enter your login credentials:\n", "blue");

    printColor("\nEnter Username: ", "yellow");
    cin >> username;

    printColor("Enter Password: ", "red");

    // Hide password input with asterisks
    char ch;
    password = "";
    while (true) {
        ch = _getch();  // Get character without displaying it
        if (ch == 13)  // If Enter is pressed (ASCII code 13)
            break;
        else if (ch == 8) {  // If Backspace is pressed (ASCII code 8)
            if (password.length() > 0) {
                password.pop_back();  // Remove last character
                cout << "\b \b";  // Delete the last asterisk displayed
            }
        } else {
            password += ch;  // Add character to password
            cout << "*";  // Display asterisk
        }
    }

    // Check if the credentials are correct
    if (username == correctUsername && password == correctPassword) {
        printColor("\nLogin successful!\n", "green");
        return true;
    } else {
        printColor("\nInvalid credentials. Please try again.\n", "red");
        return false;
    }
}

//------------------------------------------------------------------------

// Function to display the contents of the CSV file

void displayCSV(const string &filePath)
{
    ifstream file(filePath);
    string line;
    vector<vector<string>> data;

    if (!file.is_open()) {
        cout << "Error opening the file!" << endl;
        return;
    }

    while (getline(file, line)) {
        stringstream ss(line);
        string value;
        vector<string> row;
        while (getline(ss, value, ',')) {
            row.push_back(value);
        }
        data.push_back(row);
    }

    file.close();

    cout << "\nDisplaying the contents of the CSV file:\n";
    for (const auto &row : data) {
        for (const auto &val : row) {
            cout << val << "\t";
        }
        cout << endl;
    }
}

//------------------------------------------------------------------------

// Function to add a new product (with more details) to the CSV file

void addProduct(const string &filePath)
{
    string orderID, orderDate, shipDate, shipMode, customerID, customerName;
    string segment, country, city, state, postalCode, region, productID;
    string category, subCategory, productName, sales;

    cout << "\nEnter Order ID: ";
    cin >> orderID;
    cin.ignore(numeric_limits<streamsize>::max(), '\n');  // Clear the buffer


    cout << "Enter Order Date (YYYY-MM-DD): ";
    getline(cin, orderDate);


    cout << "Enter Ship Date (YYYY-MM-DD): ";
    getline(cin, shipDate);


    cout << "Enter Ship Mode: ";
    getline(cin, shipMode);


    cout << "Enter Customer ID: ";
    getline(cin, customerID);

    cout << "Enter Customer Name: ";
    getline(cin, customerName);


    cout << "Enter Segment: ";
    getline(cin, segment);


    cout << "Enter Country: ";
    getline(cin, country);


    cout << "Enter City: ";
    getline(cin, city);


    cout << "Enter State: ";
    getline(cin, state);

    cout << "Enter Postal Code: ";
    getline(cin, postalCode);

    cout << "Enter Region: ";
    getline(cin, region);

    cout << "Enter Product ID: ";
    getline(cin, productID);


    cout << "Enter Category: ";
    getline(cin, category);


    cout << "Enter Sub-Category: ";
    getline(cin, subCategory);


    cout << "Enter Product Name: ";
    getline(cin, productName);


    cout << "Enter Sales: ";
    getline(cin, sales);


    // Open the file in append mode to add the new product

    ofstream file(filePath, ios::app);
    if (!file.is_open())
    {
        cout << "Error opening the file to add product!" << endl;

        return;
    }

    file << orderID << "," << orderDate << "," << shipDate << "," << shipMode << ","
         << customerID << "," << customerName << "," << segment << "," << country << ","
         << city << "," << state << "," << postalCode << "," << region << ","
         << productID << "," << category << "," << subCategory << "," << productName << ","
         << sales << endl;

    file.close();

    printColor("\nProduct added successfully!\n", "green");
}

//------------------------------------------------------------------------


// Function to count total number of products

void totalNumberOfProducts(const string &filePath)
{
    ifstream file(filePath);
    string line;
    int productCount = 0;

    if (!file.is_open())
    {
        cout << "Error opening the file!" << endl;

        return;
    }

    while (getline(file, line))
    {

        productCount++;

    }

    cout << "\nTotal number of products: " << productCount << endl;
    file.close();

}
//------------------------------------------------------------------------


// Function to display most popular products

void mostPopularProducts(const string &filePath)
{

    cout << "\nDisplaying most popular products (not implemented, but you can add logic here).\n";

}

//------------------------------------------------------------------------

// Function to display a list of customers

void displayCustomers(const string &filePath)
{
    ifstream file(filePath);

    string line;

    set<string> customerNames;  // Using a set to store unique customer names

    if (!file.is_open())
    {
        cout << "Error opening the file!" << endl;

        return;
    }

    // Skipping the header row if it exists

    getline(file, line);  // Assuming first line is header

    // Read the CSV line by line

    while (getline(file, line))
    {
        stringstream ss(line);

        string value;

        int col = 0;

        string customerName;

        // Iterate through the columns

        while (getline(ss, value, ','))
        {
            // Customer Name is in column 6, assuming 0-based indexing

            if (col == 5)
            {

                customerName = value;  // Capture customer name

            }

            col++;
        }

        // Insert customer name into set to ensure uniqueness

        if (!customerName.empty())
        {

            customerNames.insert(customerName);

        }
    }

    file.close();

    // Display the unique customers

    if (customerNames.empty())
    {
        cout << "No customers found in the file." << endl;
    }
    else
    {
        cout << "\nList of unique customers:\n";

        for (const auto& name : customerNames)
        {

            cout << name << endl;

        }
    }
}


//------------------------------------------------------------------------

// Function to confirm exit from the program

bool confirmExit()
{
    char choice;

    cout << "\nAre you sure you want to exit? (y/n): ";

    cin >> choice;

    if (choice == 'y' || choice == 'Y')
    {
        cout<<"\n\n\n\n\n";
    // Display Footer information

    displayFooter();

        return true;

    }

    return false;
}

//------------------------------------------------------------------------


void updateProduct(const string &filePath)
{
    ifstream inputFile(filePath);

    stringstream buffer;

    string line;

    string productID;

    bool productFound = false;


    if (!inputFile.is_open())
    {
        cout << "Error opening the file for reading: " << filePath << endl;

        return;
    }

    // Read the product ID from the user

    cout << "Enter the Product ID to update: ";

    cin >> productID;

    // Read all lines from the file and store them in the buffer

    while (getline(inputFile, line))
        {

        stringstream ss(line);

        string value;

        vector<string> row;

        while (getline(ss, value, ','))
        {

            row.push_back(value);

        }

        // Assuming Product ID is in the 12th column (index 11)

        if (row[12] == productID)
        {
            productFound = true;

            cout << "Product found. Enter new details for the product.\n";

            cout << "Enter new Product Name: ";

            cin.ignore();  // To discard the newline character left in the buffer

            getline(cin, row[15]);  // Update the product name (16th column)

            cout << "Enter new Price: ";

            cin >> row[16];  // Update the price (17th column)

            // Write the updated product to the buffer

            for (size_t i = 0; i < row.size(); ++i)
            {
                buffer << row[i];
                if (i != row.size() - 1)
                {
                    buffer << ",";  // Add commas between values
                }
            }
            buffer << endl;
        }

        else
        {
            // If not found, just copy the line as is

            buffer << line << endl;
        }
    }

    inputFile.close();

    if (productFound) {
        // Try to open the file for writing
        ofstream outputFile(filePath);
        if (!outputFile.is_open()) {
            cout << "Error opening the file to overwrite: " << filePath << endl;
            return;
        }

        // Write the content from the buffer back to the file
        outputFile << buffer.str();
        outputFile.close();

        cout << "Product updated successfully!" << endl;
    } else {
        cout << "Product not found!" << endl;
    }
}

//------------------------------------------------------------------------


// Function to search a product by Product ID or Product Name

void searchProduct(const string &filePath)
 {
    ifstream inputFile(filePath);

    string line;

    string searchTerm;

    bool productFound = false;


    if (!inputFile.is_open())
    {
        cout << "Error opening the file!" << endl;

        return;  // Early exit if file cannot be opened

    }

    // Ask the user what they want to search for

    cout << "Enter the product ID or product name to search: ";

    cin >> searchTerm;

    // Read through the file and search for the term

    while (getline(inputFile, line))
    {
        stringstream ss(line);

        string value;

        vector<string> row;

        // Parse the CSV line into a row

        while (getline(ss, value, ','))
        {
            row.push_back(value);
        }

        // Assuming the product ID is in the first column and the product name is in the second column

        if (row[12] == searchTerm || row[15] == searchTerm)
        {
            productFound = true;

            cout << "\nProduct Found!" << endl;

            cout << "Product ID: " << row[12] << endl;

            cout << "Product Name: " << row[15] << endl;

            cout << "Price: " << row[16] << endl;

            cout << "Category: " << row[13] << endl;  // Assuming category is in the 4th column

            break;
        }
    }

    if (!productFound)
    {

        cout << "No product found matching the search term: " << searchTerm << endl;

    }

    inputFile.close();

}
//------------------------------------------------------------------------

// Function to split string based on a delimiter (CSV parsing)

vector<string> split(const string &line, char delimiter)
{
    vector<string> result;

    stringstream ss(line);

    string temp;

    while (getline(ss, temp, delimiter))
    {

        result.push_back(temp);

    }

    return result;
}


//------------------------------------------------------------------------


// Function to convert a string date to time_t (to make comparisons easier)

time_t convertToTimeT(const string& dateStr)
 {
    struct tm tm = {};

    stringstream ss(dateStr);

    // Parse the date using std::get_time (C++11)

    ss >> std::get_time(&tm, "%d-%m-%Y");

    // Check if parsing was successful

    if (ss.fail())
    {
        cerr << "Invalid date format: " << dateStr << endl;

        return -1;  // Invalid date
    }

    return mktime(&tm);

}

//------------------------------------------------------------------------


// Function to sort products based on order date (column 10) and display product ID and order date

void sortProductsByOrderDate(const string &filePath)
{
    ifstream file(filePath);

    string line;

    vector<pair<string, time_t>> products;  // To hold product ID and order date

    // Skip the header line

    if (!getline(file, line))
    {
        cerr << "Error reading the file or empty file." << endl;

        return;
    }

    // Read each line from the CSV and extract product ID and order date
    while (getline(file, line))
    {
        vector<string> columns = split(line, ',');

        // Ensure there are at least 10 columns
        if (columns.size() > 9)
        {
            string productID = columns[12];  // Product ID (column 13, zero-based index 12)

            string orderDateStr = columns[1];  // Order Date (column 10, zero-based index 9)

            // Convert the order date to time_t
            time_t orderDate = convertToTimeT(orderDateStr);

            if (orderDate != -1)
            {  // Only if the date is valid

                products.push_back(make_pair(productID, orderDate));

            }

            else
            {
                cerr << "Skipping product " << productID << " due to invalid order date." << endl;
            }

          }

             else
          {
            cerr << "Skipping invalid row due to insufficient columns: " << line << endl;
          }

    }

    file.close();

    // Sort products based on order date (in ascending order)

    sort(products.begin(), products.end(), [](const pair<string, time_t> &a, const pair<string, time_t> &b)
    {

        return a.second < b.second;  // Sort in ascending order of order date

    }
    );

    // Display the sorted result

    cout << "Product ID | Order Date" << endl;

    cout << "---------------------" << endl;

    for (const auto &product : products)
    {
        // Convert time_t back to string for display

        char dateStr[100];

        strftime(dateStr, sizeof(dateStr), "%Y-%m-%d", localtime(&product.second));

        cout << product.first << " | " << dateStr << endl;
    }
}

//------------------------------------------------------------------------


//TOTAL SUM AMOUNT CALUCLATION:-

//----------------------------------------------
// Define a struct to store Product ID and Sales

struct ProductSum
{
    string productID;

    int sales;

};
//----------------------------------------------

// Comparison function to sort products based on sales in descending order

bool compareSales(const ProductSum& a, const ProductSum& b)
{

    return a.sales > b.sales;  // Sort in descending order

}

//------------------------------------------------------------------------
 // TO CALCULATE TOTAL SALES AMOUNT

void readAndSortCSVFile1(const string& filePath1)
{
    ifstream file(filePath1);

    string line;

    vector<ProductSum> products;

    int totalSales = 0;  // Variable to store the sum of sales

    // Check if file is opened successfully

    if (!file.is_open())
    {

    cout << "Error opening file! Check the file path." << endl;

        return;

    }

    // Skip the header row

    getline(file, line);

    // Read and process each line in the CSV file

    while (getline(file, line))
    {
        stringstream ss(line);

        string cell;

        ProductSum product;

        // Extract Product ID (First column)

        getline(ss, product.productID, ',');

        // Extract Sales value (Second column)

        getline(ss, cell, ',');

        // Trim spaces from sales value

        while (isspace(cell.back()))
        {

            cell.pop_back(); // Remove trailing spaces

        }

        // Convert the Sales string to an integer

        try
        {
            product.sales = stoi(cell);  // Convert sales value to integer

        }
        catch (const invalid_argument& e)
        {
            cout << "Invalid sales value for product " << product.productID << ": " << cell << endl;

            product.sales = 0;  // If the sales value is invalid, set it to 0

        }

        // Add the product to the vector

        products.push_back(product);

        // Accumulate the sales value to totalSales

        totalSales += product.sales;
    }

    file.close();

    // Sort the products based on sales (in descending order)

    sort(products.begin(), products.end(), compareSales);

    // Print the total sales sum

    cout << "\nTotal Sales: " << totalSales << endl;

}

//---------------------------------------------------

//AVG ORDER PER DAY :-
//-------------------------------------------

struct Order
{
    string productID;

    string orderDate;

    int sales;
};

//------------------------------------------
// CALCULATE AVERAGE ORDER PER DAY

void calculateAverageOrdersPerDay(const string& filePath)
{
    ifstream file(filePath);

    string line;

    vector<Order> orders;

    set<string> uniqueDates;  // To store unique order dates

    // Check if file is opened successfully

    if (!file.is_open())
    {
        cout << "Error opening file! Check the file path." << endl;

        return;
    }

    // Skip the header row

    getline(file, line);

    // Read and process each line in the CSV file

    while (getline(file, line))
    {
        stringstream ss(line);

        string cell;

        Order order;

        // Extract Product ID (First column)

        getline(ss, order.productID, ',');

        // Extract Order Date (Second column)

        getline(ss, order.orderDate, ',');

        // Extract Sales value (Third column)

        getline(ss, cell, ',');

        // Trim spaces from sales value

        while (isspace(cell.back()))
        {

            cell.pop_back(); // Remove trailing spaces

        }

        // Convert the Sales string to an integer

        try
        {
            order.sales = stoi(cell);  // Convert sales value to integer

        } catch (const invalid_argument& e)
        {
            cout << "Invalid sales value for product " << order.productID << ": " << cell << endl;

            order.sales = 0;  // If the sales value is invalid, set it to 0
        }

        // Add the order to the vector and store the order date

        orders.push_back(order);

        uniqueDates.insert(order.orderDate);  // Add order date to the set
    }

    file.close();

    // Calculate total orders and unique days

    int totalOrders = orders.size();

    int uniqueDays = uniqueDates.size();

    if (uniqueDays == 0)
    {
        cout << "No orders found!" << endl;

        return;

    }

    // Calculate average orders per day

    double averageOrdersPerDay = static_cast<double>(totalOrders) / uniqueDays;

    // Output the result

    cout << "Total Orders: " << totalOrders << endl;

    cout << "Unique Days: " << uniqueDays << endl;

    cout << "Average Orders Per Day: " << averageOrdersPerDay << endl;


}

//------------------------------------------------------------------------

// TOTAL SUM CALCULATION OF SLAES:-
//-----------------------------------------

// Define a struct to store Product ID and total Sales

struct ProductSales
{
    string productID;

    int totalSales;

};

//------------------------------------------

void displayMostInDemandProduct(const string& filePath1)
{
    ifstream file(filePath1);

    string line;

    unordered_map<string, int> productSalesMap;  // Map to store total sales for each product

    // Check if file is opened successfully

    if (!file.is_open())
    {
        cout << "Error opening file! Check the file path." << endl;

        return;
    }

    // Skip the header row

    getline(file, line);

    // Read and process each line in the CSV file

    while (getline(file, line))
    {
        stringstream ss(line);

        string cell;

        string productID;

        int sales;

        // Extract Product ID (First column)

        getline(ss, productID, ',');

        // Extract Sales value (Second column)

        getline(ss, cell, ',');

        // Trim spaces from sales value

        while (isspace(cell.back()))
        {

            cell.pop_back(); // Remove trailing spaces

        }

        // Convert the Sales string to an integer

        try
        {
            sales = stoi(cell);  // Convert sales value to integer


        }
         catch (const invalid_argument& e)
        {
            cout << "Invalid sales value for product " << productID << ": " << cell << endl;

            sales = 0;  // If the sales value is invalid, set it to 0

        }

        // Add the sales to the respective product's total sales

        productSalesMap[productID] += sales;


    }

    file.close();

    // Find the product with the maximum sales

    string mostInDemandProductID;

    int maxSales = 0;

    for (const auto& entry : productSalesMap)
    {
        if (entry.second > maxSales)
        {
            mostInDemandProductID = entry.first;

            maxSales = entry.second;
        }
    }

    // Display the most in-demand product

    if (mostInDemandProductID.empty())
    {

        cout << "No data available." << endl;

    }

    else
    {
        cout << "Most In-Demand Product (with the Maximum Orders):" << endl;

        cout << "Product ID: " << mostInDemandProductID << " | Total Sales: " << maxSales << endl;

    }

}


//------------------------------------------------------------------------

//SORT BASED ON SALES:-
//------------------------------------------


void readAndSortCSVFile(const string& filePath1)
{
    ifstream file(filePath1);

    string line;

    vector<ProductSum> products;

    // Check if file is opened successfully

    if (!file.is_open())
    {
        cout << "Error opening file! Check the file path." << endl;

        return;
    }

    // Skip the header row

    getline(file, line);

    // Read and process each line in the CSV file

    while (getline(file, line))
        {
        stringstream ss(line);

        string cell;

        ProductSum product;

        // Extract Product ID (First column)

        getline(ss, product.productID, ',');

        // Extract Sales value (Second column)

        getline(ss, cell, ',');

        // Trim spaces from sales value

        while (isspace(cell.back()))
        {

            cell.pop_back(); // Remove trailing spaces

        }

        // Convert the Sales string to an integer

        try
        {

            product.sales = stoi(cell);  // Convert sales value to integer

        }
        catch (const invalid_argument& e)
        {
            cout << "Invalid sales value for product " << product.productID << ": " << cell << endl;

            product.sales = 0;  // If the sales value is invalid, set it to 0

        }

        // Add the product to the vector

        products.push_back(product);


    }

    file.close();

    // Sort the products based on sales (in descending order)

    sort(products.begin(), products.end(), compareSales);

    // Print the sorted products (Product ID and Sales)

    cout << "Product ID | Sales" << endl;

    cout << "--------------------" << endl;

    for (const auto& product : products)
    {

        cout << product.productID << " | " << product.sales << endl;

    }
}

//------------------------------------------------------------------------


void displayProductNamesFromColumn16(const std::string& filePath)
{
    // Open the CSV file

    std::ifstream file(filePath);

    // Check if the file is opened successfully

    if (!file.is_open())
    {

        std::cerr << "Could not open the file!" << std::endl;

        return;
    }

    std::string line;

    // Read the file line by line

    while (getline(file, line))
        {

        std::stringstream ss(line);  // Use stringstream to split the line by commas

        std::string columnValue;

        int columnIndex = 0;

        // Loop through each column (separated by commas

        while (getline(ss, columnValue, ','))
        {
            columnIndex++;

            // Check if we are at column 16 (remember index starts from 0)

            if (columnIndex == 16)
            {

                std::cout << "Product Name : " << columnValue << std::endl;

                break;  // Exit the loop once we've found the column 16 value

            }

        }

    }


    // Close the file
    file.close();


}


//------------------------------------------------------------------------


/*THIS IS THE COMPLETE PRODUCT MODULE FUNTCTION HERE IS THE FUNCTION WHICH SELECTS WHAT SHOULD BE DONE */


int module1()

{


 // Display the front cover page with dynamic animations

    displayFrontPage();

    //THIS PATH IS FOR PRODCUT MODULE TO RETRIVE AND APPLY OPERATIONS ON IT...

    string filePath = "C:\\Users\\Admin\\OneDrive\\Dokumen\\DAAPROJECT\\ECOMMERCE\\ecommerce.csv";

    // THIS PATH IS TO PERFORM OPERATIONS PARTICULARLY ON SALES...

     string filePath1 = "C:\\Users\\Admin\\OneDrive\\Dokumen\\DAAPROJECT\\ECOMMERCE\\Book1.csv";

    bool returnToMenu = false;  // Control flag for returning to menu

    // Step 1: User Login

    bool isLoggedIn = false;

    while (!isLoggedIn)
    {
        isLoggedIn = login();  // Attempt login

        if (!isLoggedIn)
        {
            printColor("\nPlease try again after checking your username and password.\n", "yellow\n");

            sleep(2); // Adding a slight delay before retrying
        }
    }

    // Step 2: Show Menu after successful login

    int userChoice = -1;

    while (userChoice != 0)
    {
        printColor("\n=== E-Commerce System Menu ===\n", "blue");

        cout << "1. Display CSV Contents\n\n\n";

        cout << "2. Add a Product\n\n\n";

        cout << "3. Update a Product\n\n\n";

        cout << "4. Sort Product by Sales\n\n\n";

        cout << "5. Search a Product\n\n\n";

        cout << "6. Sort Products by OrderDate\n\n\n";

        cout << "7. Total  SalesAmount\n\n\n";

        cout << "8. Average NO OF orders perDay\n\n\n";

        cout << "9. Display Most Popular Product\n\n\n";

        cout << "10. Display Customers\n\n\n";

        cout << "11. Total Number of Products\n\n\n";  // New option for total number of products

        cout << "12. Names of  Products\n\n\n";  // New option for total number of products

        cout << "13. Exit\n\n\n";

        printColor("\nEnter your choice (1-12): \n\n\n", "yellow");

        cin >> userChoice;

        switch (userChoice)
        {
            case 1:

                cout << "\nYou chose to display the CSV contents...\n\n" << endl;

                displayCSV(filePath);
                break;


            case 2:

                cout << "\nYou chose to add a product...\n\n" << endl;

                addProduct(filePath);
                break;

            case 3:

                // Update product functionality

                 updateProduct(filePath);  // Calls updateProduct but doesn't exit
                 break;

            case 4:

                 // Path to your CSV file (with escape characters for backslashes)

                  readAndSortCSVFile(filePath1);
                  break;

            case 5:

               searchProduct(filePath);
                break;


            case 6:

               sortProductsByOrderDate(filePath);
                break;


            case 7:

               readAndSortCSVFile1(filePath1);
               break;

            case 8:

                 calculateAverageOrdersPerDay(filePath);
                break;


            case 9:

                displayMostInDemandProduct(filePath1);
                break;

            case 10:

                displayCustomers(filePath);
                break;

            case 11:

                totalNumberOfProducts(filePath);
                break;

            case 12:

            displayProductNamesFromColumn16(filePath);
                break;

            case 13:

                if (confirmExit())
                {
                    printColor("\nExiting system...\n\n", "red");

                    return 0;
                }
                break;


            default:

                printColor("\nInvalid choice. Please enter a valid option (1-12).\n\n", "red");
                break;



        }


        // Reset the returnToMenu flag after each operation

        returnToMenu = false;

    }

return 0;

}

//THIS MARKS THE COMPLETION OF PRODUCT MODULE...........


//------------------------------------------------------------------------

//THIS MARKS THE BEGINNING OF STOCK MANAGEMENT.......

//THIS CONTAINS THE HEADER FILE OF MODULE2.

#include <iostream>

#include <fstream>

#include <sstream>

#include <map>

#include <string>

#include <cstdlib>

#include <queue>

#include <climits>
 // For INT_MAX

#include <unistd.h>
 // For sleep (to create delay)



using namespace std;


// Define colors for terminal output

//--------------------------------

//THIS HAS COLOUS HEADERLIBRARY

#define RESET   "\033[0m"

#define BOLD    "\033[1m"

#define BLUE    "\033[34m"

#define GREEN   "\033[32m"

#define CYAN    "\033[36m"

#define YELLOW  "\033[33m"

#define RED     "\033[31m"

#define MAGENTA "\033[35m"
// Added new color

#define WHITE   "\033[37m"
 // Added new color


// Define Product structure

struct Product
{

    string product_id;

    string name;

    double price;

    int quantity;



    // Default constructor

    Product() :
        product_id(""), name(""), price(0.0), quantity(0) {}


    // Constructor to initialize Product

    Product(string id, string n, double p, int q)

        : product_id(id), name(n), price(p), quantity(q) {}

};


// Define Inventory class

class Inventory
{

private:


    map<string, Product> products;  // Use map for inventory, key is product_id

    queue<string> restockQueue;  // Queue for restocking products

public:

    // Function to read data from CSV file and populate the inventory

    void loadDataFromFile(const string& filePath)
    {

        ifstream file(filePath.c_str());  // Open the file

        string line;

        // Skip header line if CSV has headers

        getline(file, line);

        while (getline(file, line))
        {

            string order_id, order_date, ship_date, ship_mode, customer_id;

            string customer_name, segment, country, city, state, postal_code;

            string region, product_id, category, sub_category, product_name, sales_str;

            double sales;

            int quantity = 0;  // Quantity, assuming quantity comes from a sales calculation

            // Create a stringstream to parse each line

            stringstream ss(line);



            // Read data from CSV line (based on the order of columns)
            getline(ss, order_id, ',');

            getline(ss, order_date, ',');

            getline(ss, ship_date, ',');

            getline(ss, ship_mode, ',');

            getline(ss, customer_id, ',');

            getline(ss, customer_name, ',');

            getline(ss, segment, ',');

            getline(ss, country, ',');

            getline(ss, city, ',');

            getline(ss, state, ',');

            getline(ss, postal_code, ',');

            getline(ss, region, ',');

            getline(ss, product_id, ',');

            getline(ss, category, ',');

            getline(ss, sub_category, ',');

            getline(ss, product_name, ',');

            getline(ss, sales_str, ',');

            // Convert sales to double

            sales = atof(sales_str.c_str());


            // Assuming sales value correlates to quantity
            quantity = static_cast<int>(sales);

            // Assuming 1 sale = 1 product sold

            // Trim leading and trailing spaces from product_id and product_name

            product_id = trim(product_id);

            product_name = trim(product_name);

            // Add product to inventory (map)

            if (!product_id.empty())
            {

                if (products.find(product_id) != products.end())
                {

                    products[product_id].quantity += quantity;

                }

                else
                {

                    products[product_id] = Product(product_id, product_name, sales, quantity);

                }

            }

        }

    }






    // Helper function to trim leading and trailing spaces from a string

    string trim(const string& str)
    {

        size_t first = str.find_first_not_of(" \t\n\r\f\v");

        size_t last = str.find_last_not_of(" \t\n\r\f\v");

        return (first == string::npos || last == string::npos) ? "" : str.substr(first, (last - first + 1));
    }


    // Function to save inventory data to the CSV file

    void saveDataToFile(const string& filePath)
    {
        ofstream file(filePath.c_str());
        // Open the file for saving

        file << "OrderID,OrderDate,ShipDate,ShipMode,CustomerID,CustomerName,Segment,Country,City,State,PostalCode,Region,ProductID,Category,SubCategory,ProductName,Sales" << endl;

        for (auto& it : products)
        {
            Product p = it.second;
            // Access the value (Product) from the map

            // Write to the file in the specified CSV format

                 file << "1," << "Order-12345," << "12-12-2024," << "15-12-2024," << "Standard,"

                 << "CUST-001," << "John Doe," << "Consumer," << "USA," << "New York," << "NY," << "10001," << "North,"

                 << p.product_id << ",CategoryX,SubCategoryY," << p.name << "," << p.price * p.quantity << endl;

        }

    }

//------------------------------------------------------------
    // Add or update product in inventory

    void addOrUpdateProduct(const string& product_id, const string& name, double price, int quantity)
    {

        auto it = products.find(product_id);


        if (it != products.end())
        {
            // Update the quantity if the product already exists

            it->second.quantity += quantity;


            // Optional: Update the price if needed (you can remove this if price is fixed)

            if (price > 0)
            {

                it->second.price = price;

            }

            cout << GREEN << "Product updated: " << name << " (ID: " << product_id << ") with additional quantity: "

                 << quantity << RESET << endl;

        }

        else

        {
            // Add a new product

            products[product_id] = Product(product_id, name, price, quantity);

            cout << GREEN << "New product added: " << name << " (ID: " << product_id << ")" << RESET << endl;

        }

    }


//-------------------------------------------

    // Process a sale
    void processSale(const string& product_id, int quantity)
    {

        // Check if the product exists in the inventory

        auto it = products.find(product_id);

        if (it != products.end())
        {

            Product& product = it->second; // Reference to the product

            // Check if sufficient stock is available

            if (product.quantity >= quantity)
            {

                product.quantity -= quantity; // Reduce stock

                // Display a detailed confirmation message

                cout << GREEN << "Sale processed successfully!" << RESET << endl;

                cout << GREEN << "Product: " << product.name << " (ID: " << product_id << ")" << RESET << endl;

                cout << GREEN << "Quantity sold: " << quantity << RESET << endl;

                cout << GREEN << "Remaining stock: " << product.quantity << RESET << endl;

            }
            else
            {

                // Handle insufficient stock

                cout << RED << "Error: Insufficient stock for product " << product.name

                     << " (ID: " << product_id << ")." << RESET << endl;

                cout << RED << "Requested: " << quantity << ", Available: " << product.quantity << RESET << endl;

                // Suggest restocking

                cout << YELLOW << "Suggestion: Consider restocking this product." << RESET << endl;

            }

        }

        else
        {

            // Handle the case where the product does not exist

            cout << RED << "Error: Product with ID " << product_id << " not found in the inventory." << RESET << endl;

            // Provide guidance for adding the product

            cout << CYAN << "Hint: Use the 'Add or Update Product' option to add this product to the inventory." << RESET << endl;

        }

    }


//-----------------------------------------------------------------

    // Process a product return

    void processReturn(const string& product_id, int quantity)
    {

        // Check if the product exists in the inventory

        auto it = products.find(product_id);


        if (it != products.end())
        {

            Product& product = it->second; // Reference to the product

            // Validate the quantity being returned

            if (quantity > 0)

            {

                product.quantity += quantity; // Increase stock

                // Display a detailed confirmation message

                cout << CYAN << "Return processed successfully!" << RESET << endl;

                cout << CYAN << "Product: " << product.name << " (ID: " << product_id << ")" << RESET << endl;

                cout << CYAN << "Quantity returned: " << quantity << RESET << endl;

                cout << CYAN << "Updated stock: " << product.quantity << RESET << endl;


                // Suggest checking stock levels

                cout << YELLOW << "Suggestion: Verify the updated stock level to ensure accuracy." << RESET << endl;

            }

            else

            {
                // Handle invalid return quantities

                cout << RED << "Error: Invalid return quantity (" << quantity << "). Quantity must be positive." << RESET << endl;

                cout << CYAN << "Hint: Please ensure the quantity entered is greater than zero." << RESET << endl;

            }

        }

        else

        {

            // Handle the case where the product does not exist

            cout << RED << "Error: Product with ID " << product_id << " not found in the inventory." << RESET << endl;


            // Provide guidance for adding the product

            cout << CYAN << "Hint: Use the 'Add or Update Product' function to add this product to the inventory." << RESET << endl;

        }

    }

//---------------------------------------------

    // Get current stock of a product

    void getCurrentStock(const string& product_id)
    {

        // Attempt to find the product

        auto it = products.find(product_id);


        if (it != products.end())
        {

            const Product& product = it->second;
            // Reference to the product

            cout << YELLOW << "Product Information:" << RESET << endl;

            cout << YELLOW << "Name: " << product.name << RESET << endl;

            cout << YELLOW << "ID: " << product_id << RESET << endl;

            cout << YELLOW << "Current Stock: " << product.quantity << RESET << endl;

            cout << YELLOW << "Price per Unit: $" << product.price << RESET << endl;

            // Provide additional suggestions

            if (product.quantity < 10)
            {

                cout << RED << "Warning: Stock for " << product.name << " is running low!" << RESET << endl;

                cout << CYAN << "Hint: Consider restocking soon." << RESET << endl;


            }


            else
            {

                cout << GREEN << "Stock levels are sufficient." << RESET << endl;

            }

        }

        else

        {


            // Handle case where product is not found

            cout << RED << "Error: Product with ID " << product_id << " not found in the inventory." << RESET << endl;

            cout << CYAN << "Hint: Use the 'Add or Update Product' function to add this product to the inventory." << RESET << endl;

        }

    }

//----------------------------------------------------------


    // Restock a product

    void restock(const string& product_id, int quantity)
    {

        // Attempt to find the product

        auto it = products.find(product_id);


        if (it != products.end())

        {

            Product& product = it->second; // Reference to the product

            // Validate the restock quantity

            if (quantity > 0)
            {

                product.quantity += quantity; // Increase stock

                // Detailed success message

                cout << BLUE << "Restock Successful!" << RESET << endl;

                cout << BLUE << "Product Name: " << product.name << RESET << endl;

                cout << BLUE << "Product ID: " << product_id << RESET << endl;

                cout << BLUE << "Quantity Added: " << quantity << RESET << endl;

                cout << BLUE << "Updated Stock: " << product.quantity << RESET << endl;

                // Suggest verifying current stock

                cout << YELLOW << "Suggestion: Check current stock levels for accuracy." << RESET << endl;

            }
            else

            {

                // Handle invalid restock quantities

                cout << RED << "Error: Invalid restock quantity (" << quantity << "). Quantity must be positive." << RESET << endl;

                cout << CYAN << "Hint: Please enter a restock quantity greater than zero." << RESET << endl;

            }

        }
        else

        {

            // Handle case where product is not found

            cout << RED << "Error: Product with ID " << product_id << " not found in the inventory." << RESET << endl;

            cout << CYAN << "Hint: Use the 'Add or Update Product' function to add this product to the inventory before restocking." << RESET << endl;

        }

    }


//---------------------------------------------------------------


    // Add product to restocking queue based on some priority (for example, low stock)

    void addForRestocking(const string& product_id)
    {

        // Attempt to find the product

        auto it = products.find(product_id);

        if (it != products.end())
        {

            const Product& product = it->second;

            // Check if the product is already in the queue

            if (product.quantity >= 10)
            {

                cout << GREEN << "Product " << product.name << " has sufficient stock. No need to restock." << RESET << endl;

                return;

            }

            // Add to restock queue

            restockQueue.push(product_id);

            cout << YELLOW << "Product " << product.name << " has been added to the restocking queue." << RESET << endl;

        }
        else
        {

            // Handle case where product is not found

            cout << RED << "Error: Product with ID " << product_id << " not found in the inventory." << RESET << endl;

        }

    }


//----------------------------------------------------------


    // Process restocking from queue

    void processRestocking()
    {

        cout << MAGENTA << "---- Processing Restocking Queue ----" << RESET << endl;

        // Check if the restock queue is empty

        if (restockQueue.empty())

        {

            cout << CYAN << "Restocking queue is empty. No products to restock." << RESET << endl;

            return;

        }

        // Process all products in the restock queue

        while (!restockQueue.empty())

        {

            string product_id = restockQueue.front();

            restockQueue.pop();

            auto it = products.find(product_id);

            if (it != products.end())

            {

                Product& product = it->second;

                // Restock only if the product has low stock

                if (product.quantity < 10)

                {

                    int restock_quantity = 100; // Restock by 100 units

                    restock(product_id, restock_quantity);

                    cout << GREEN << "Restocking completed for " << product.name << "." << RESET << endl;

                }

                else

                {

                    cout << YELLOW << "Skipping restocking for " << product.name << " as it has sufficient stock." << RESET << endl;
                }

            }
            else

            {

                cout << RED << "Error: Product with ID " << product_id << " not found in inventory. Skipping..." << RESET << endl;

            }

        }

        cout << CYAN << "All products in the restocking queue have been processed." << RESET << endl;

    }


//------------------------------------------------------------------

    // Display all products in inventory

    void displayInventory()

    {

        cout << MAGENTA << "---- Current Inventory ----" << RESET << endl;

        if (products.empty())

        {

            cout << CYAN << "No products available in inventory." << RESET << endl;

            return;
        }

        for (const auto& it : products)

        {

            const Product& product = it.second;

            // Display detailed product information

            cout << BLUE << "Product ID: " << product.product_id << RESET << endl;

            cout << "    Name: " << product.name << endl;

            cout << "    Price: $" << product.price << endl;

            cout << "    Quantity: " << product.quantity << endl;


            // Highlight low-stock products

            if (product.quantity < 10)

            {

                cout << RED << "    Warning: Low stock!" << RESET << endl;

            }

        }


        cout << CYAN << "End of inventory list." << RESET << endl;


    }


//-------------------------------------------------------

    void displayTotalProducts()
     {

    int totalProducts = 0;

    int lowStockCount = 0;

    for (const auto& it : products)
    {

        totalProducts++;

        if (it.second.quantity < 10)

        {

            lowStockCount++;

        }

    }

    cout << CYAN << "Total number of products in inventory: " << totalProducts << RESET << endl;

    if (lowStockCount > 0)

        {

        cout << YELLOW << "Number of products with low stock (less than 10 units): " << lowStockCount << RESET << endl;

        cout << CYAN << "Hint: Consider restocking low-stock products to avoid shortages." << RESET << endl;

        }
     else

        {

        cout << GREEN << "All products have sufficient stock levels." << RESET << endl;

         }

}



};


//=================================================================

    // Function to check and display the total number of products available

  void displayFrontPagep()
   {

    // Welcome banner
    cout << BOLD << CYAN
         << "===================================================================" << RESET << endl;

    cout << BOLD << YELLOW
         << "              Welcome to the Advanced Inventory Management System" << RESET << endl;

    cout << BOLD << CYAN
         << "===================================================================" << RESET << endl;

    // ASCII art for a visually appealing welcome
    cout << BOLD << GREEN
         << "        ____        _        _                  _                \n"
         << "       / ___|  __ _| |_ __ _| |__   __ _ ___   (_) ___ ___  _ __ \n"
         << "       \\___ \\ / _` | __/ _` | '_ \\ / _` / __|  | |/ __/ _ \\| '_ \\ \n"
         << "        ___) | (_| | || (_| | | | | (_| \\__ \\  | | (_| (_) | | | |\n"
         << "       |____/ \\__,_|\\__\\__,_|_| |_|\\__,_|___/  |_|\\___\\___/|_| |_|\n"
         << RESET << endl;

    // System features
    cout << BOLD << MAGENTA << "\nSystem Features:" << RESET << endl;

    cout << GREEN << "  - Add, update, and delete products seamlessly." << RESET << endl;

    cout << GREEN << "  - Real-time tracking of inventory levels." << RESET << endl;

    cout << GREEN << "  - Generate sales and restocking reports." << RESET << endl;

    cout << GREEN << "  - User-friendly navigation with detailed logs." << RESET << endl;

    cout << GREEN << "  - Automated alerts for low-stock items." << RESET << endl;

    // Motivational message

    cout << BOLD << BLUE

         << "\nLet's revolutionize the way you manage your inventory!" << RESET << endl;

    cout << BOLD << YELLOW

         << "Your success begins here." << RESET << endl;

    // Instructions

    cout << BOLD << MAGENTA << "\nQuick Start Guide:" << RESET << endl;

    cout << CYAN << " 1. Use the menu options to perform inventory tasks.\n"
         << " 2. Keep your product information updated.\n"
         << " 3. Regularly check reports for better decision-making.\n"
         << " 4. Use the restocking feature to maintain stock levels.\n"
         << RESET << endl;

    // Detailed instructions for each feature

    cout << BOLD << GREEN << "Feature Instructions:" << RESET << endl;

    cout << YELLOW << "- Adding Products:" << RESET << endl;

    cout << "  Enter the product ID, name, price, and quantity to add a new product." << endl;

    cout << YELLOW << "- Updating Products:" << RESET << endl;

    cout << "  Use the product ID to update details like name, price, or quantity." << endl;

    cout << YELLOW << "- Sales Processing:" << RESET << endl;

    cout << "  Select a product and specify the quantity sold to update stock." << endl;

    cout << YELLOW << "- Restocking:" << RESET << endl;

    cout << "  Use the restocking feature to replenish stock levels automatically." << endl;

    // Navigation help

    cout << BOLD << MAGENTA << "\nNavigation Help:" << RESET << endl;

    cout << CYAN << "Use the following keys to navigate the menu:\n"
         << "  [1] Add a product\n"
         << "  [2] Update a product\n"
         << "  [3] View current inventory\n"
         << "  [4] Process a sale\n"
         << "  [5] Restock a product\n"
         << "  [6] Generate reports\n"
         << "  [7] Exit the system\n" << RESET << endl;

    // Placeholder for system checks

    cout << BOLD << MAGENTA << "\nSystem Status:" << RESET << endl;

    cout << GREEN << "All systems are functioning correctly." << RESET << endl;

    cout << GREEN << "Database connection: ACTIVE" << RESET << endl;

    cout << GREEN << "Inventory tracking: ENABLED" << RESET << endl;

    cout << GREEN << "Notifications: ON" << RESET << endl;

    // Placeholder for user interaction

    cout << BOLD << YELLOW
         << "\nEnter your credentials to continue." << RESET << endl;

    cout << CYAN << "Loading user dashboard..." << RESET << endl;

    // Pause for dramatic effect

    for (int i = 0; i < 3; i++)
    {
        cout << ".";
        sleep(1);  // Simulate loading process
    }
    cout << endl;

    // Encouraging message
    cout << BOLD << BLUE
         << "\nThank you for choosing the Advanced Inventory Management System!" << RESET << endl;

    cout << BOLD << YELLOW
         << "We're here to make your business thrive!" << RESET << endl;

    // Footer
    cout << BOLD << CYAN
         << "\n===================================================================" << RESET << endl;
    cout << BOLD << YELLOW
         << "                     System Ready for Use" << RESET << endl;
    cout << BOLD << CYAN
         << "===================================================================" << RESET << endl;

    // Additional pause for readability
    sleep(2);
}


//-----------------------------------------------------------------------------------
//-----------------------------------------------------------------------------------



//THIS PART OF THE MODULE2 WILL HAS MAIN FUNCTION()


    int module2()

    {

        string filePath ="C:\\Users\\Admin\\OneDrive\\Dokumen\\DAAPROJECT\\ECOMMERCE\\ecommerce.csv" ; // Specify your file path here

        // Display the front page

    displayFrontPagep();

        Inventory inventory;

        // Load data from CSV file into inventory

        inventory.loadDataFromFile(filePath);


        int choice;

        string product_id, name;

        double price;

        int quantity;

        do
        {

            // Display menu options

            cout << "\n" << CYAN << "--- Inventory Management System ---" << RESET << endl;

            cout << GREEN << "1. Add or Update Product" << RESET << endl;

            cout << GREEN << "2. Process Sale" << RESET << endl;

            cout << GREEN << "3. Process Return" << RESET << endl;

            cout << GREEN << "4. Get Current Stock" << RESET << endl;

            cout << GREEN << "5. Restock Product" << RESET << endl;

            cout << GREEN << "6. Add Product for Restocking" << RESET << endl;

            cout << GREEN << "7. Process Restocking" << RESET << endl;

            cout << GREEN << "8. Display Inventory" << RESET << endl;

            cout << GREEN << "9. Display Total Number of Products" << RESET << endl;

            cout << RED << "10. Exit" << RESET << endl;

            cout << BLUE << "Enter your choice: " << RESET;

            cin >> choice;

            cin.ignore();  // To ignore the newline character after the choice

            switch (choice)
            {

            case 1:

                cout << "Enter Product ID: ";

                cin >> product_id;

                cout << "Enter Product Name: ";

                cin.ignore();
                // To ignore the newline left by previous input

                getline(cin, name);

                cout << "Enter Product Price: ";

                cin >> price;

                cout << "Enter Quantity: ";

                cin >> quantity;

                inventory.addOrUpdateProduct(product_id, name, price, quantity);

                break;


            case 2:

                cout << "Enter Product ID: ";

                cin >> product_id;

                cout << "Enter Quantity: ";

                cin >> quantity;

                inventory.processSale(product_id, quantity);  // Process sale

                break;


            case 3:

                cout << "Enter Product ID: ";

                cin >> product_id;

                cout << "Enter Quantity: ";

                cin >> quantity;

                inventory.processReturn(product_id, quantity);  // Process return

                break;


            case 4:

                cout << "Enter Product ID: ";

                cin >> product_id;

                inventory.getCurrentStock(product_id);  // Get current stock

                break;


            case 5:

                cout << "Enter Product ID: ";

                cin >> product_id;

                cout << "Enter Quantity to Restock: ";

                cin >> quantity;

                inventory.restock(product_id, quantity);  // Restock product

                break;


            case 6:

                cout << "Enter Product ID to Add for Restocking: ";

                cin >> product_id;

                inventory.addForRestocking(product_id);  // Add for restocking

                break;


            case 7:
                inventory.processRestocking();  // Process restocking

                break;


            case 8:
                inventory.displayInventory();  // Display inventory

                break;


            case 9:

                inventory.displayTotalProducts();  // Display total number of products

                break;

            case 10:

                // Save the inventory data back to CSV file

                inventory.saveDataToFile(filePath);


                cout << GREEN << "Exiting... Data saved to file.\n\n" << RESET << endl;

                break;

            default:

                cout << RED << "Invalid choice! Please try again." << RESET << endl;

            }

        }

        while (choice != 10);


        return 0;



    }

//-----------------------------------------------------------------------
//THIS MARKS THE END OF STOCK MANAGEMENT SYSTEM.


//-----------------------------------------------------------------------

// THIS MARKS THE START OF ORDER MANAGEMENT MODULE......


#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <vector>
#include <queue>
#include <unordered_map>
#include <stdexcept>
#include <iomanip> // For std::setprecision and std::fixed
#include <ctime> // For date comparison
#include <sstream> // For std::get_time

using namespace std;

//----------------------------------------------------------


// Order class definition
class Order3
{

public:
    // Unique identifier for the order
    string orderID;

    // Date when the order was placed
    string orderDate;

    // Date when the order was shipped
    string shipDate;

     // Mode of shipping, e.g., Standard, Express
    string shipMode;

    // Unique identifier for the customer
    string customerID;

    // Name of the customer who placed the order
    string customerName;

    // Segment of the customer (e.g., Consumer, Corporate)
    string segment;

    // Country where the order is being delivered
    string country;

    // City where the order is being delivered
    string city;

    // State where the order is being delivered
    string state;

    // Postal code for the delivery address
    string postalCode;

     // Region for tracking
    string region;

     // Unique identifier for the product
    string productID;

    // Product category
    string category;

    // Sub-category of the product
    string subCategory;

    // Name of the product ordered
    string productName;

    // Fixed price or discount associated with the order

    double fixed;

    // Order tracking attributes

    // Current status of the order (e.g., Not Shipped, Shipped, Delivered)
    string orderStatus;

    // The current location of the order (e.g., In Transit, Delivered)
    string currentLocation;

    // Additional tracking information (optional)
    string trackingInfo;

    // Default constructor
    Order3()
        : orderID(""), orderDate(""), shipDate(""), shipMode(""), customerID(""), customerName(""),
          segment(""), country(""), city(""), state(""), postalCode(""), region(""), productID(""),
          category(""), subCategory(""), productName(""), fixed(0.0), orderStatus("Not Shipped"),
          currentLocation("Warehouse"), trackingInfo("") {}

    // Parametrized constructor for creating an order from given values
    Order3(string id, string date, string shipD, string mode, string cID, string cName,
          string seg, string cntry, string city, string st, string pCode, string region,
          string pID, string cat, string subCat, string pName, double fixedValue, string status)
        : orderID(id), orderDate(date), shipDate(shipD), shipMode(mode), customerID(cID),
          customerName(cName), segment(seg), country(cntry), city(city), state(st),
          postalCode(pCode), region(region), productID(pID), category(cat), subCategory(subCat),
          productName(pName), fixed(fixedValue), orderStatus(status), currentLocation("Warehouse"),
          trackingInfo("") {}

    // Method to display all details about the order
    void display() const {
        cout << "Order ID: " << orderID << endl;
        cout << "Order Date: " << orderDate << endl;
        cout << "Ship Date: " << shipDate << endl;
        cout << "Ship Mode: " << shipMode << endl;
        cout << "Customer ID: " << customerID << endl;
        cout << "Customer Name: " << customerName << endl;
        cout << "Segment: " << segment << endl;
        cout << "Country: " << country << endl;
        cout << "City: " << city << endl;
        cout << "State: " << state << endl;
        cout << "Postal Code: " << postalCode << endl;
        cout << "Region: " << region << endl;
        cout << "Product ID: " << productID << endl;
        cout << "Category: " << category << endl;
        cout << "Sub-Category: " << subCategory << endl;
        cout << "Product Name: " << productName << endl;
        cout << fixed << setprecision(2) << "Fixed: " << fixed << endl;
        cout << "Order Status: " << orderStatus << endl;
        cout << "Current Location: " << currentLocation << endl;
        cout << "Tracking Info: " << trackingInfo << endl;
    }

    // Method to update the order status to a new value
    void updateStatus(const string& status, const string& location)
     {
        // Check if the status is valid
        if (status == "Shipped" || status == "Out for Delivery" || status == "Delivered")
            {
                orderStatus = status;

                // Update the current location of the order
                currentLocation = location;
            }
        else
            {
                cout << "Invalid status!" << endl;
            }
    }

    // Method to calculate days between two dates, useful for tracking shipping times
    static int calculateDaysDifference(const string& date1, const string& date2)
    {
        struct tm tm1 = {}, tm2 = {};

        // Use std::get_time to parse the date strings into tm structures
        istringstream ss1(date1), ss2(date2);
        ss1 >> get_time(&tm1, "%Y-%m-%d");
        ss2 >> get_time(&tm2, "%Y-%m-%d");

        if (ss1.fail() || ss2.fail())
            {
                cerr << "Error parsing date!" << endl;

                // Return an error value if parsing fails
                return -1;
            }

        // Convert tm to time_t
        time_t time1 = mktime(&tm1);
        time_t time2 = mktime(&tm2);

        if (time1 == -1 || time2 == -1)
            {
                cerr << "Error converting dates to time_t!" << endl;
                return -1;
            }

        // Calculate the difference in seconds and convert to days
        double seconds = difftime(time2, time1);

        // Return the days difference
        return static_cast<int>(seconds / (60 * 60 * 24));
    }
};

// Function to read data from a CSV file and return a vector of Orders
vector<Order3> readOrdersFromCSV(const string& filePath)
 {
    // Vector to store orders
    vector<Order3> orders;

    // Open the file
    ifstream file(filePath);

    string line;

    // Check if the file is open
    if (!file.is_open())
        {
            // Handle file opening failure
            throw runtime_error("Could not open the file!");
        }

    // Skip the header line (if any)
    getline(file, line);

    // Read each line from the CSV and create an Order object
    while (getline(file, line))
        {
            stringstream ss(line);
            string orderID, orderDate, shipDate, shipMode, customerID, customerName;
            string segment, country, city, state, postalCode, region, productID;
            string category, subCategory, productName;
            double fixedValue;

            // Parse each line using commas as separators
            getline(ss, orderID, ',');
            getline(ss, orderDate, ',');
            getline(ss, shipDate, ',');
            getline(ss, shipMode, ',');
            getline(ss, customerID, ',');
            getline(ss, customerName, ',');
            getline(ss, segment, ',');
            getline(ss, country, ',');
            getline(ss, city, ',');
            getline(ss, state, ',');
            getline(ss, postalCode, ',');
            getline(ss, region, ',');
            getline(ss, productID, ',');
            getline(ss, category, ',');
            getline(ss, subCategory, ',');
            getline(ss, productName, ',');
            ss >> fixedValue;

            // Create an Order object and add it to the orders vector
            orders.push_back(Order3(orderID, orderDate, shipDate, shipMode, customerID, customerName,
                               segment, country, city, state, postalCode, region, productID,
                               category, subCategory, productName, fixedValue, "Not Shipped"));
    }

    // Close the file
    file.close();

    // Return the vector of orders
    return orders;
}

// A simple structure to represent an order queue and hash map
class OrderModule
{
private:
    // To store orders in FIFO order
    queue<Order3> orderQueue;

    // To store orders by order ID
    unordered_map<string, Order3> orderMap;

public:
    // Add a new order to the queue and the hash map
    void createOrder(const Order3& order3)
    {
        // Push to queue for FIFO processing
        orderQueue.push(order3);

        // Add the order to the hash map
        orderMap[order3.orderID] = order3;
    }

    // Update an order by order ID
    void updateOrder(const string& orderID)
     {
        if (orderMap.find(orderID) != orderMap.end())
            {
                // Ask the user whether to set the order status to 'Shipped', 'Out for Delivery' or 'Delivered'
                string newStatus, newLocation;
                cout << "Select new status for Order ID " << orderID << ":" << endl;
                cout << "1. Shipped" << endl;
                cout << "2. Out for Delivery" << endl;
                cout << "3. Delivered" << endl;
                cout << "Enter choice (1/2/3): ";
                int statusChoice;
                cin >> statusChoice;

                // Set the status based on the user's choice
                if (statusChoice == 1)
                    {
                        newStatus = "Shipped";
                        newLocation = "In Transit";
                    }
                else if (statusChoice == 2)
                    {
                        newStatus = "Out for Delivery";
                        newLocation = "In Delivery Truck";
                    }
                else if (statusChoice == 3)
                    {
                        newStatus = "Delivered";
                        newLocation = "Delivered";
                    }
                else
                    {
                        cout << "Invalid choice!" << endl;
                        return;
                    }

            // Update the order's status
            orderMap[orderID].updateStatus(newStatus, newLocation);
            cout << "Order status updated to " << newStatus << "!" << endl;
        }
        else
            {
                cout << "Order with ID " << orderID << " not found!" << endl;
            }
    }

    // View order by order ID
    void viewOrder(const string& orderID)
     {
        if (orderMap.find(orderID) != orderMap.end())
            {
                orderMap[orderID].display();
                // Calculate the days difference between order date and current date

                // For example, current date
                string currentDate = "2025-01-03";

                int days = Order3::calculateDaysDifference(orderMap[orderID].orderDate, currentDate);
                cout << "Days since order was placed: " << days << " days" << endl;
        }
        else
            {
                cout << "Order with ID " << orderID << " not found!" << endl;
            }
    }

    // Display all orders in the queue
    void displayOrders()
    {
        while (!orderQueue.empty())
            {
                orderQueue.front().display();

                // Remove the order from the queue after displaying
                orderQueue.pop();
                cout << "-------------------------------" << endl;
            }
    }
};

int module3()
 {
    string filePath = "C:\\Users\\Admin\\OneDrive\\Dokumen\\DAAPROJECT\\ECOMMERCE\\ecommerce.csv";

    // Creating an order module
    OrderModule orderModule;
    try
     {
        // Read orders from the CSV file
        vector<Order3> orders = readOrdersFromCSV(filePath);

        // Create orders in the order module
        for (const auto& order3 : orders)
            {
                // Add each order to the system
                orderModule.createOrder(order3);
            }

        int choice;
        string orderID;
        bool exit = false;

        // Main loop for user input
        while (!exit)
            {
                cout << "\nSelect an operation:" << endl;
                cout << "1. Display all orders" << endl;
                cout << "2. View order by ID" << endl;
                cout << "3. Update order status" << endl;
                cout << "4. Exit" << endl;
                cout << "Enter your choice (1-4): ";
                cin >> choice;

                // Switch statement to handle user input
                switch (choice)
                 {

                    case 1:
                        {
                            // Display all orders in the system
                            orderModule.displayOrders();

                            break;
                        }

                    case 2:
                        {
                            cout << "Enter order ID to view: ";
                            cin >> orderID;

                            // View a specific order by ID
                            orderModule.viewOrder(orderID);

                            break;
                        }

                    case 3:
                        {
                            cout << "Enter order ID to update status: ";
                            cin >> orderID;

                            // Update the status of an order
                            orderModule.updateOrder(orderID);
                            break;

                        }

                    case 4:
                        {
                            cout << "Exiting program." << endl;

                            // Exit the program
                            exit = true;

                            break;
                        }

                    default:
                            cout << "Invalid choice, please enter a number between 1 and 4." << endl;
            }
        }
    }
    catch (const runtime_error& e)
    {
        // Handle file opening or other runtime errors
        cerr << "Error: " << e.what() << endl;
    }

    return 0;
}




  //END OF ORDER MANAGEMENT MODULE......
//-----------------------------------------------------------------------

// THIS MARKS THE START OF REPORT AND ANALYSIS MODULE.


#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <map>
#include <vector>
#include <numeric>
#include <cmath>
#include <iomanip>
#include <algorithm>
#include <limits>

using namespace std;



// Constants
// Conversion rate from USD to INR
const double conversionRate = 75.0;

//-------------------------------------------------

// Function to convert string "YYYY-MM" to an integer representing
//the month count (e.g., 2023-01 -> 1, 2023-02 -> 2, etc.)
int monthToInt(const string& monthYear)
 {
    int year, month;
    sscanf(monthYear.c_str(), "%4d-%2d", &year, &month);

    // Assuming data starts from 2023
    return (year - 2023) * 12 + month;
}

//-------------------------------------------------


// Function to display the most expensive product
void displayMostExpensiveProduct(const string& product, double sales, double conversionRate)
 {
    if (!product.empty())
        {
            cout << "The most expensive product is: " << product
                << " with sales of $" << sales << " (Rs:" << sales * conversionRate << ")" << endl;
        }
    else
        {
            cout << "No valid data found in the file for the most expensive product." << endl;
        }
}

//-------------------------------------------------


// Function to display the least expensive product
void displayLeastExpensiveProduct(const string& product, double sales)
 {
    if (!product.empty())
        {
            cout << "The least expensive product is: " << product
                << " with sales of $" << sales << " (Rs:" << sales * conversionRate << ")" << endl;
        }
    else
        {
            cout << "No valid data found in the file for the least expensive product." << endl;
        }
}

//-------------------------------------------------


// Function to display total number of items in inventory
void displayTotalItems(int totalItems)
{
    cout << "Total number of items in inventory: " << totalItems << endl;
}

//-------------------------------------------------


// Function to display total sales
void displayTotalSales(double totalSales)
 {
    cout << "Total Sales: $" << totalSales << " (Rs:" << totalSales * conversionRate << ")" << endl;
}


//-------------------------------------------------

// Function to display total orders
void displayTotalOrders(int totalOrders)
{
    cout << "Total Orders: " << totalOrders << endl;
}

//-------------------------------------------------


// Function to display average order value (AOV)
void displayAverageOrderValue(double aov)
{
    cout << "Average Order Value (AOV): $" << aov << " (Rs:" << aov * conversionRate << ")" << endl;
}


//-------------------------------------------------

// Function to display sales growth trend analysis (Month-to-Month)
void displaySalesGrowthTrend(const map<string, double>& monthlySales)
 {
     // Set output to 2 decimal places
    cout << fixed << setprecision(2);
    cout << "Sales Growth Trend Analysis (Month-to-Month):\n";
    cout << "Month    | Sales (USD) | Sales (INR)  | Growth (%)\n";
    cout << "----------------------------------------------------\n";

    double previousSales = 0.0;

    for (const auto& entry : monthlySales)
        {
            const string& monthYear = entry.first;
            double currentMonthSales = entry.second;
            double currentMonthSalesINR = currentMonthSales * conversionRate;

        if (previousSales != 0.0)
            {
                double growth = ((currentMonthSales - previousSales) / previousSales) * 100;
                cout << monthYear << " | $" << currentMonthSales << " | Rs:" << currentMonthSalesINR
                << " | " << growth << "%" << endl;
            }
        else
            {
                cout << monthYear << " | $" << currentMonthSales << " | Rs:" << currentMonthSalesINR
                << " | N/A" << endl;
            }

            // Update the previous month's sales
            previousSales = currentMonthSales;
    }
}

//-------------------------------------------------


// Function to display revenue prediction for next month
void displayRevenuePrediction(double predictedRevenueUSD, double predictedRevenueINR, int nextMonth)
{
    cout << "Predicted Revenue for Next Month (Month " << nextMonth << "): $" << predictedRevenueUSD
     << " (Rs:" << predictedRevenueINR << ")" << endl;
}


//-------------------------------------------------

// Function to display total sales by region
void displayTotalSalesByRegion(const map<string, double>& regionSales)
 {
     // Set output to 2 decimal places
    cout << fixed << setprecision(2);
    cout << "Total Sales by Region:" << endl;

    string highestRegion, lowestRegion;

    // Using numeric_limits
    double maxRegionSales = 0.0, minRegionSales = numeric_limits<double>::max();

    for (const auto& entry : regionSales)
        {
        cout << "Region: " << entry.first << " - Sales: $" << entry.second
        << " (Rs:" << entry.second * conversionRate << ")" << endl;

        // Find the region with highest sales
        if (entry.second > maxRegionSales)
            {
                maxRegionSales = entry.second;
                highestRegion = entry.first;
            }

        // Find the region with lowest sales
        if (entry.second < minRegionSales)
            {
                minRegionSales = entry.second;
                lowestRegion = entry.first;
            }
        }

    // Display the highest sales region
    cout << "\nRegion with Highest Sales: " << highestRegion << " - Sales: $" << maxRegionSales
     << " (Rs:" << maxRegionSales * conversionRate << ")" << endl;

     // Display the lowest sales region
    cout << "Region with Lowest Sales: " << lowestRegion << " - Sales: $" << minRegionSales
    << " (Rs:" << minRegionSales * conversionRate << ")" << endl;
}


//-------------------------------------------------

// Function to display total sales by sub-category
void displayTotalSalesBySubCategory(const map<string, double>& subCategorySales)
 {
     // Set output to 2 decimal places
    cout << fixed << setprecision(2);
    cout << "Total Sales by Sub-category:" << endl;
    for (const auto& entry : subCategorySales)
        {
        cout << "Sub-category: " << entry.first << " - Sales: $" << entry.second
        << " (Rs:" << entry.second * conversionRate << ")" << endl;
    }
}

//-------------------------------------------------

//THIS IS THE MAIN FUNCTION....

int module4()
 {
    // File path
    string filePath = "C:/Users/Admin/OneDrive/Dokumen/DAAPROJECT/ECOMMERCE/ecommerce.csv";

    // Open the file
    ifstream file(filePath);

    // Check if the file opened successfully
    if (!file.is_open())
        {
            cerr << "Error: Could not open the file at " << filePath << endl;
            return 1;
        }

    string line, productName, mostExpensiveProduct, leastExpensiveProduct;

    // Lowest and highest values to start comparison
    double maxSales = numeric_limits<double>::lowest(), minSales = numeric_limits<double>::max();

    int totalItems = 0;
    double totalSales = 0.0;
    int totalOrders = 0;
    // Map to store total sales for each product
    map<string, double> productSales;

    // Map to store total sales for each month (YYYY-MM)
    map<string, double> monthlySales;

     // Map to store total sales for each region
    map<string, double> regionSales;

    // Map to store total sales for each sub-category
    map<string, double> subCategorySales;

    // Read the header line (if any)
    // Skip the first line (header)
    getline(file, line);

    // Read the file line by line
    while (getline(file, line))
        {
            // Increment total items count
            totalItems++;

        stringstream ss(line);
        string orderId, orderDate, shipDate,
                    shipMode, customerId, customerName,
                    segment, country, city, state, postalCode,
                    region, productId, category, subCategory,
                    productNameTemp, salesStr;

        // Parse each column (assuming columns are always in the same order)
        getline(ss, orderId, ',');
        getline(ss, orderDate, ',');
        getline(ss, shipDate, ',');
        getline(ss, shipMode, ',');
        getline(ss, customerId, ',');
        getline(ss, customerName, ',');
        getline(ss, segment, ',');
        getline(ss, country, ',');
        getline(ss, city, ',');
        getline(ss, state, ',');
        getline(ss, postalCode, ',');
        getline(ss, region, ',');
        getline(ss, productId, ',');
        getline(ss, category, ',');
        getline(ss, subCategory, ',');
        getline(ss, productNameTemp, ',');
        getline(ss, salesStr, ',');

        // Convert sales to double
        double sales;
        try
        {
            sales = stod(salesStr);
            totalSales += sales;

             // Increment total orders count
            totalOrders++;
        }
        catch (...)
        {
            cerr << "" << line << endl;
            continue;
        }

        // Update total sales for the product
        productSales[productNameTemp] += sales;

        // Check if this product is the most expensive
        if (sales > maxSales)
            {
                maxSales = sales;
                mostExpensiveProduct = productNameTemp;
            }

        // Check if this product is the least expensive
        if (sales < minSales)
            {
                minSales = sales;
                leastExpensiveProduct = productNameTemp;
            }

        // Extract the month and year for monthly sales
        // YYYY-MM format
        string monthYear = orderDate.substr(0, 7);
        monthlySales[monthYear] += sales;

        // Update the total sales for this region
        regionSales[region] += sales;

        // Update the total sales for this sub-category
        subCategorySales[subCategory] += sales;
    }

    // Close the file
    file.close();

    // Calculate Average Order Value
    double averageOrderValue = (totalOrders > 0) ? (totalSales / totalOrders) : 0.0;

    // Prepare data for linear regression
    // X values (months)
    vector<int> months;

    // Y values (sales for each month)
    vector<double> salesValues;

    for (const auto& entry : monthlySales)
        {
            months.push_back(monthToInt(entry.first));
            salesValues.push_back(entry.second);
        }

    // Perform Linear Regression to find slope (m) and intercept (b)
    int n = months.size();
    double sumX = accumulate(months.begin(), months.end(), 0);
    double sumY = accumulate(salesValues.begin(), salesValues.end(), 0.0);
    double sumXY = 0.0, sumX2 = 0.0;

    for (int i = 0; i < n; ++i)
        {
            sumXY += months[i] * salesValues[i];
            sumX2 += months[i] * months[i];
        }

    // Calculate slope (m) and intercept (b)
    double m = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX);
    double b = (sumY - m * sumX) / n;

    // Predict next month's revenue (next month = max(months) + 1)
    int nextMonth = *max_element(months.begin(), months.end()) + 1;
    double predictedRevenueUSD = m * nextMonth + b;
    double predictedRevenueINR = predictedRevenueUSD * conversionRate;

    int choice;
    while (true)
        {
            cout << "\nEnter your choice:" << endl;
            cout << "1: Display the most expensive product" << endl;
            cout << "2: Display the least expensive product" << endl;
            cout << "3: Display total number of items in inventory" << endl;
            cout << "4: Display total sales" << endl;
            cout << "5: Display total orders" << endl;
            cout << "6: Display average order value (AOV)" << endl;
            cout << "7: Display sales growth trend analysis (Month-to-Month)" << endl;
            cout << "8: Display revenue prediction for next month" << endl;
            cout << "9: Display total sales by region" << endl;
            cout << "10: Display total sales by sub-category" << endl;
            cout << "11: Exit" << endl;
            cin >> choice;

        // Output the results using switch case
        switch (choice)
         {
            case 1:
                displayMostExpensiveProduct(mostExpensiveProduct, maxSales, conversionRate);
                break;
            case 2:
                displayLeastExpensiveProduct(leastExpensiveProduct, minSales);
                break;
            case 3:
                displayTotalItems(totalItems);
                break;
            case 4:
                displayTotalSales(totalSales);
                break;
            case 5:
                displayTotalOrders(totalOrders);
                break;
            case 6:
                displayAverageOrderValue(averageOrderValue);
                break;
            case 7:
                displaySalesGrowthTrend(monthlySales);
                break;
            case 8:
                displayRevenuePrediction(predictedRevenueUSD, predictedRevenueINR, nextMonth);
                break;
            case 9:
                displayTotalSalesByRegion(regionSales);
                break;
            case 10:
                displayTotalSalesBySubCategory(subCategorySales);
                break;
            case 11:
                cout << "Exiting the program." << endl;
                return 0;
            default:
                cout << "Invalid choice. Please enter a number between 1 and 11." << endl;
                break;
        }
    }

    return 0;
}




//THIS MARKS THE END OF 4TH MODULE:REPORT AND ANALYSIS.......

//----------------------------------------------------------------------



  //THIS IS THE INTEGRATION OF ALL MODULES MAIN FUNCTION......

int main()
{    // Display Banner

displayBanner();


// Display Description of the System

displayDescription();

    // Display Features of the System

displayFeatures();

// Display Instructions for users

displayInstructions();

// Proceed to the main menu after the intro

int userChoice = -1;

while (userChoice != 0)

{
        delayPrint("***....Enter 1: PRODUCT MODULE..***  \n",1);
        delayPrint("***....Enter 2: STOCK MODULE..***  \n",1);
        delayPrint("***....Enter 3: ORDER MODULE..***  \n",1);
        delayPrint("***....Enter 4: REPORT ANALYSIS  MODULE..***  \n",1);
        delayPrint("***....Enter 5: TO SHUTDOWN THE SYSTEM..***  \n",1);
        delayPrint("***....Enter Your CHOICE ->....***  \n",1);

        cin >> userChoice;

      switch (userChoice)

      {
           setColor(3);

          case 1:
                  module1();
                  continue;

          case 2:

                module2();
                  continue;

          case 3:
                  module3();
                  continue;

          case 4:

                    module4();

                  continue;

          case 5:

              cout<<"  THANK-YOU VISIT AGAIN......................\n\n";
              break;

          default: cout<<" moye moye ENTER VALID CHOICE  \n\n";
              break;

      }

    return 0;
}


}






//   THANKYOU .............  HAVE A NICE DAY.
