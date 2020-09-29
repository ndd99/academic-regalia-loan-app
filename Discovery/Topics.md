# Topics Discussed
Introductions, Graham explained his role and the role of Dr. Melinda Messineo. Graham explained the basic idea of the project specifically how the user works and a few specific systems, loaners and borrowers. Emphasis on dates available.
fault in last project was automation, but the system made too many assumptions and did not account for human error. single click confirmations should be a solution. We are to take portions of the old code, polish it and work from there. 
Framework must be updated.emphasis on maintainability. If mistakes noticed in old program fix first. Brevin asks if how integrated this will be with the bsu website. Graham explains that last year bsu sso was attempted but did not work because time did not allow it.
as far as integration goes the end goal is to have it fully integrated with bsu.edu. we will need to meet with the network security admin to help in terms of SSO and related APIs. They are already familiar with the project. 
temp login system may be needed. backend is in php, framework is cakePHP ver 3, must be updated to ver 4 if we continue with it, which Graham recommends. He also recommends some other framework for forms, and less or sass for css. 
Brevin asked how database maintenance will be performed, whether by bsu or on our own. Keith asked if we would be able to load our own docker images, Graham said we would have access through AWS. He does not recommend AWS. Evan asked how notification would work if by email or otherwise. 
Graham says that was an issue with the previous group, would recommend email/text notifications. Brevin asks about bsu email, and StarRes. Nick asked about a mobile responsive version. Graham says mobile is pretty low priority, but will speak with Dr. Messineo. 
The userbase will likely be on a computer in their ball state office, but we should keep the option open. Graham explained the purpose of the project. helps new faculty to save money and effort by allowing a loan system. 
Evan asked about the UI if anything needs to be changed, Graham asked about our confidence in graphic design, brevin and evan said they were somewhat confident. graham reccomends Bootstrap to help UI. might look generic but that's not a big deal. 
the current site is fine but can be improved. Graham recommends a complete bootstrap overhaul of the project. Graham mentioned that we may need to get some source of funding for 
text message notifications if we cannot get push notifications to work the way we would like. The biggest issue with the application right now is getting the person who listed the item and the person reserving the item in touch to pick up or return an item.

# Things Clarified
Look over old project and discuss prototyping. make plans to talk to network security, for SSO and production server. next meeting October 23rd 12:00 tentatively.
