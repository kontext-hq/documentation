

# GDPR Overview

!!! question "Have Suggestion?"

    Kindly drop us a line at [support@kontext.in](mailto:support@kontext.in)



The GDPR (General Data Protection Regulation) is set to take effect May 25, 2018, and its regulations apply to any company, person, or group that collects, processes, or otherwise handles the personal data of EU and UK residents.

## Kontext, GDPR, and you

The GDPR defines two different types of organizations who have to follow the new regulations: data controllers and data processors.

- **Data controllers** determine why and how personal data is processed. As a Kontext customer, your organization is considered a data controller.
- **Data processors** process user data on behalf of the controller. Kontext processes user data on your behalf, which makes us a data processor.

As a processor, we provide the technical capabilities and organizational processes that will allow you, our customers, to maintain the rights of your EU and UK users while using our product.

See below for some common tasks to help you remain GDPR compliant while using Kontext. The information below is not legal advice. We recommend you work with a lawyer to understand exactly how GDPR applies to your organization.

## Informing your end users

As a data controller, you have to inform your end-users about the personal data you collect from them and their rights surrounding this data. The GDPR lays out several requirements for what you must inform your end-users, and it’s up to you to provide the information in a transparent, accessible way.

For more details on how Kontext handles and protects your users’ data, refer to the security information in your contract’s data processing addendum.

## User consent for data collection

GDPR sets standards (such as consent or legitimate interest) for when it's lawful to process data. It's up to you, the controller, to ensure that all the data you send to Kontext is lawful. We recommend you work with legal counsel to determine which rationale for data processing applies to you.

To prevent data collection through Kontext, do not call Kontext.start() until after the user opts-in for data collection. You can also offer separate opt-out prompts for different messaging channels in Kontext. Giving users more options to control their app experience might encourage them to consent (opt-in) to data collection.

For example, if a user opts-in to data collection in general, but not to email or push, your app should call Kontext.logoutEmail and the opt-out methods for the push and email channels. 

## Block data collection and processing

If a user objects to data processing, you can prevent Kontext from collecting and processing data for that user with the `logout` API request.

`logout` will stop Kontext from collecting data for that user moving forward. In order to ensure that Kontext does not process this user’s old data, we will delete all of their data from our systems.

For more details, please see our [logout API documentation](/android/reference#logoutemail)

## Erasing user data

Under GDPR, data subjects have the right to request the deletion or removal of personal data.

To delete a user’s data from Kontext, you can use the deleteUser request, which will delete all user profile information for that user. To also erase all historical data for the user, include the `fullErasure` flag and set it to `true`. See our API documentation for more on the deleteUser call.

!!! info "Info"

    If you export Kontext data into your backup locations, then you are responsible for handling GDPR requests in that data.

## Data access and portability

Users also have the right to request a copy of their personal data in a human or machine-readable format. The GDPR also specifies that data subjects can obtain and reuse their personal data for their own purposes (for example, to create an account with a competing service).

## Rectify user data

As a data controller, you must give users the ability to correct personal data if they feel it is inaccurate or incomplete. In Kontext, this includes user location, user attributes, and device attributes.

Use the [sendUserAttributes](/android/reference#senduserattributes) API request to change a user's attributes or location data in Kontext. 

## Additional support

If you are unsure of how to use some of the methods or processes above, contact [support@Kontext.in](mailto:support@kontext.in) for assistance. We are happy to answer any questions on how to use our platform. Of course, please do not mistake this for legal advice. If you have legal questions about the GDPR, we urge you to consult with your lawyer.