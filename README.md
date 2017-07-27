# VOLTTRON Data Monitoring and Control Application #

**General Notes/Overview**
The VOLTTRON Data Monitoring and Control Application (VOLTTRON App) is an iOS, swift-built application used for near real-time monitoring of VOLTTRON inverters and direct VOLTTRON inverter control. Currently, the VOLTTRON App only supports the iOS architecture, and is only available for iPhones 5 and greater (which will soon be moved up to the iPhone 6 and greater with iOS 11 coming out soon). Application support and maintenance is managed by the VOLTTRON App Development Team at Oak Ridge National Labs. 
* **

**Public/Key Functions**
The VOLTTRON App currently uses a layer of *Views*, managed by *View Controllers* that are meant to display and control specifics aspects of the VOLTTRON inverter. In order to provide ease of access, key functions are included underneath each *View Controller*, along with a short description. The *View Controllers* are organized by their queued appearance.

* **Login View Controller** 
    *This Controller is displayed when the application is first opened and prompts the user for a password in order to access the site.*
    * *PasswordTester(sender:)* -> This function tests the inputted password (sender.text) against the allowed passwords in the "passwords" array.
* **Graphing View Controller**
    *This Controller opens after a succesful user login. The display contains segues to the children View Controllers along with a graphical representation of the inputted data.*
    * *GrabDataFromJSON()* -> This function performs an HTTP "GET" request to pull information from the server.
    * *PostControlToServerFunction(with:)* -> This function essentially does the opposite of the GrabDataFromJSON function; it preforms an HTTP "POST" request to push data up to the server.
    * *DrawMoreImage()* -> This function is used with the "ImageView" Class to draw the graph, and display the current data. This function is/can be used in a switch/case arrangement with the *ShowSelectedImage()* function to switch between current data and user-selected data.
* **Primary Table View Controller**
    *This Controller manages all the user-input controls for the VOLTTRON inverter (i.e. Control Mode, Grid Status, Power Set Points, etc.) in a static, grouped TableView. The functions not listed here (@IB---) are all near identical: change appearance based on *Status JSON* information, and update *Control JSON* information when pressed.*
    * *Prepare(for segue:)* -> This function sends information to the child View Controller (when it's time for it to appear) and also updates the list of the *Graphing View Controllers* list of subviews.
* **Control Modes View Controller**
    *This Controller manages the items in the top-overlay of the *Raw Data Table*.*
    * *GoToSpecificCell(sender:)* -> This function takes the user-inputted value and calls the function in *Raw Data Table View Controller* that scans the saved data, finds the matching time, and displays the cell at the top of the screen.*
* **Raw Data Table View Controller**
    *This Controller handles displaying the raw data, along with managing the addition of new Table View Cells.*
    * *GoToCell(at time:)* -> This function scans through the saved data and takes the user to the specified or, if the time is larger than the amount of time passed, to the latest time.
    * *TableView(tableView:, cellForRowAt:)* -> This function assigns data to the *Table View Cell* at the specified row. 
* **

**Versions**
Please ensure that you're app version matches the current stable version before reporting errors or complaints.
* Current Stable Version: Version 1.0
* Current Supported Devices: 
    * iPhone 5
    * iPhone 5c
    * iPhone 5s
    * iPhone 6
    * iPhone 6 Plus
    * iPhone 7
    * iPhone 7 Plus
* **

**Contact**
For Help, Support, or Questions, please contact the VOLTTRON App Development Team at:
* Phone: *(865) 748-8822*
* Email: *nhk@ornl.gov*
