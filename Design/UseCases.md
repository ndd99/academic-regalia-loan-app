# Actors
* Renter
    * A Ball State faculty/staff member who is in need of some type of academic regalia item
* Rentee
    * A former or current Ball State faculty/staff member who has some type of academic regalia item they no longer need
* Admin
    * A Ball State staff member who can periodically check the listings to make sure all of them are valid, as well as answering any questions users may have about the system
# Use Cases
* UC1 List an item
    * Listing an item is one of the main purposes of this application. without the ability to do this none of the other use cases will be possible.
    * A Rentee clicks on the "List an item" button, enters some information dependent on what kind of item it is. That info is put into an SQL database and is listed on the "Items" tab of the main website.
    * BR1
* UC2 Reserve an item
    * Reserving an item is the second of the main purposes of the application.
    * A Renter finds an item they want to rent on the "Items" page of the site, and clicks the "Reserve" button next to it. They enter the date they need the item by, date they will return it, and possibly any notes they would like the rentee to know. An email notification is sent to the rentee saying an item they listed has been requested.
    * BR1
* UC3 Accept, decline or alter a reservation
    * A Rentee may not be available to rent out their regalia on the requested date, so it is important to be able to alter or decline a reservation if needed
    * When the Rentee receives an email they will be given a link to a new page to accept alter, or deny the request. If they want to accept, they can simply click the "Accept" button. If they want to deny they simply click the "Deny" button. If they want to alter the reservation they will click the "Alter" button where they will be brought to a new page similar to the one given to Renters making a request. the rentee will be able to alter the day the reservation will start, or the day it will end, as well as add a note for the renter. An email with the altered information will be sent to the renter. 
    * BR1, BR2
* UC4 Accept, decline or alter further, an altered reservation
    * A Renter may not be able to work with the altered terms given by the Rentee, thus they should be able to decline or alter the reservation further.
    * The renter will receive an email stating that a reservation they requested has been altered and will be given a link that leads them to another page similar to a reservation page. If they want to accept the alteration they can click the "accept" button. If they want to deny the reservation they click the "deny" button, and if they want to alter the reservation further they will click the "alter" button. They will be given the 2 date fields to alter as well as another notes field. from there an email will be sent to the rentee, following the same steps as in UC3.
    * BR1, BR2
* UC5 Report a website issue
    * A renter or rentee may have a question about the system, a feature request, or a bug report all of which should be sent to the admin for them to respond.
    * A renter or rentee will go to the "Contact us" page where there will be a field to type out any kind of question, feature request, or bug report they desire. below it will be a send button, when clicked will send the contents of that field to the email address of the admin. It will also include the email address of the person who sent the request in case the admin may need to contact them.
    * BR1, BR2
* UC6 Edit an item
    * A rentee may want to edit an item they have previously uploaded if they gain new information on the item
    * The rentee will go to the "My Listing" section of the dashboard where they will find the item they want to edit and click the "Edit" button next to it. They will have all the fields they saw when initially uploading the item initially. Once edited they will click the "Save Changes" button and all changes will be uploaded to the database.
    * BR1
* UC7 Delete an item
    * A rentee may decide they no longer want an item up to rent, so they may delete it.
    * The rentee will go to the "My Listing" section of the dashboard where they will find the item they want to delete. THey will click the "Delete" button next to the item, and a confirmation window will pop up. They will click the "Confirm" button, and the listing will be deleted form the database.