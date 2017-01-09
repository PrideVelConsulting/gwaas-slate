---
title: Cisco GWaaS iOS Documentation

language_tabs:
  - html
  - request
  - response

toc_footers:
  - <a href='http://www.pridevel.com'>PrideVel Consulting LLC</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# URL Endpoint

ViewController: CG_URLEndpointViewController.

```html
https://still-lowlands-39275.herokuapp.com

Method called on Next:
- (IBAction)didTapNextButton:(id)sender
```

This view is used to set the endpoint URL to which the app will point to for making API requests to.

# Login

ViewController: CG_LoginViewController.

```html
Method called on Submit:
- (void)initiateDataRequestWithMethodType:(NSString *)methodType 
andMethodName:(NSString *)methodName 
andParameters:(NSDictionary *)parameters 
andFunctionName:(NSString *)functionName 
andView:(UIView *)view 

methodType: "POST"
methodName: "sessions"
parameters: @{@"email": _emailAddressTxtField.text, 
@"password": _passwordTxtField.text}
functionName: "Login"
view: self.view

- (void)initiateDataRequestWithMethodType:(NSString *)methodType 
andMethodName:(NSString *)methodName 
andParameters:(NSDictionary *)parameters 
andFunctionName:(NSString *)functionName 
andView:(UIView *)view

methodType: "GET"
methodName: "organizations"
parameters: nil, 
functionName: "List Organizations"
view: view
```

This view is used by the user to enter his email and password to initiate the login process.

<aside class="notice">
On successful login, the apps hits the API to fetch list of organizations that
he/she owns or is a member of.
</aside>


# Organizations

ViewController: CG_OrganzationsListTableViewController.

This view is used by the user to select an organization from the list of organizations that
he/she owns or is a member of within a tableView

# Account

ViewController: CG_HomeViewController.

```html
- (void)setupDummyDataFetch
# Creates dummy data for Assets, Job Tickets, Alerts and Customers since we are
# not getting this data from APIs currently

- (void)setupUserInterface
# Creates the UI Elements for the view
```

This view displays the details of the Organization that the user selected to view.

**Sections:**

Assets Down (Also viewable by Elevators Tab).

Job Tickets.

Alerts.

Customers.

**Graphs of:**

Tickets by Priority.

Assets by Model

# Job Tickets

ViewController: CG_JobTicketsViewController

The view displays the tickets that are:

**New Installs**

```html
- (void)initiateDataRequestWithMethodType:(NSString *)methodType 
andMethodName:(NSString *)methodName 
andParameters:(NSDictionary *)parameters 
andFunctionName:(NSString *)functionName 
andView:(UIView *)view 

NSDictionary *params = @{
  @"claim_ids":[NSArray arrayWithObjects:claim_id, nil], 
  @"tags":tagValues, 
  @"address": @{
    @"address_1": self.gatewayAddressLineOneTxtField.text ? self.gatewayAddressLineOneTxtField.text : @"", 
    @"address_2": self.gatewayAddressLineTwoTxtField.text ? self.gatewayAddressLineTwoTxtField.text : @"", 
    @"city": self.gatewayAddressCityTxtField.text ? self.gatewayAddressCityTxtField.text : @"", 
    @"state": self.gatewayAddressStateTxtField.text ? self.gatewayAddressStateTxtField.text : @"", 
    @"zipcode": self.gatewayAddressZipCodeTxtField.text ? self.gatewayAddressZipCodeTxtField.text : @""
  }
};

methodType: "CLAIM"
methodName: "organizations/%ld/claims"
parameters: params, 
functionName: "Claim Device"
view: view
```

Options: 

Map, 

Ticket, 

Install
ViewController: CG_AddAssetViewController.

The view provides the user the option to Scan Code via Barcode Scanner within the app
or enter the Serial # or Invoice ID via the textfield.

Along with that the User can enter the address as well as fill/select values for tags.

Finally they can claim the device.

*Maintenance*

Options: Map, Ticket, Test

*Replace*

Options: Map, Ticket, Test

*Completed*

The view has two sections either view via tableView or Map

# Alerts

ViewController: CG_AlertsViewController.

This view displays the alerts and allows the user to interact with Support Desk on Spark

```html
- (NSArray<UITableViewRowAction *> *)tableView:(UITableView *)tableView 
  editActionsForRowAtIndexPath:(NSIndexPath *)indexPath
# Contains the code to open a specific Spark Room
```

# Customers

ViewController: CG_ManagedCustomersViewController.

This view displays the list of Customers, Address and # of Gateways

# Elevators

ViewController: CG_AssetsViewController.

The view displays the assets that are

**Claimed**

**Down**

**Active**

and has tableView and MapView based data display

# Settings

ViewController: CG_SettingsTableViewController.

Displays the Current Endpoint URL and option to Log Out.
