# Print Shop App

## Required functionalities

### Public App

#### Print editing

A user (logged in or anonymous) is able to create and edit a print order, by:

- selecting from a collection of predefined templates
- adding custom content:
  - upload image / crop / rotate / move / resize / color adjustment
  - text / select font / color / size / alignment / rotation
  - simple shapes / rectangle, circle, triangle, line / resize / rotate / color
- uploading a complete document in a recognized format (word, pdf, jpg, etc.)
- editing the print media (type, thickness)
- editing order options (quantity, delivery, contact info, etc.)
- exporting order in portable format (e.g. svg)

#### Tenant whitelabel

A Tenant user is able to onboard a subdomain (or path slice, TBD) of the main app and edit look and feel elements:

- App name
- Logo
- color scheme

A Tenant user is able to view certain statistical reports regarding the activity on their respective Tenant.

#### Order management

A user (logged in or anonymous) is able to pay online using a card processor (including receipt management).

A user (logged in or anonymous) is able to view the details of the last order, in any intermediate state (i.e. before or after being paid / processed / delivered)

A logged in user is able to view a history of past orders.

#### Blog

A user (logged in or anonymous) is able to see a presentation page with articles order chronologically, with a search option.

### Admin App

#### Order management

An Admin user is able to add, edit, delete templates.

An Admin user is able to view, edit, change status of orders in any intermediate state.

An Admin user is able to export an order in a format suitable for processing.

#### Tenant management

An Admin user is able to approve a Tenant onboarding submission.

An Admin user is able to suspend a Tenant, effectively making their sub-URL inaccessible.

#### Blog / CMS

An Admin user is able to add / edit / delete articles in the presentation page.

#### Reporting

An Admin user is able to view certain statistical reports regarding the app operation, with slices per tenant.

### Common / Utilities

#### User management

The app is able to securely register and sign in users as Customers.

The app provides the appropriate tools for GDPR regulation enforcement.

The app is able to securely sign in Admin users.

#### Integration with ERP

The app is able to call REST APIs to the ERP, providing:

- accounting information
- stock availability

#### Logging

The app logs all interactions and allows an Admin user (or, possibly a DevOps engineer) to retrieve specific logs by time, topic, or other logging characteristics.

## Deployment

![Deployment diagram](https://www.plantuml.com/plantuml/svg/VOxTIiGm48Nlvob2lTvNa9MwY1T2SPyWpOmra2P3EcafuhkRfhjkkw1NytE-mpd7GNIKr3imBYHKLLr64yDeaMAbzA2CKr-0MdIh1rBLAv8NA_CUiiZgmTdkKrgNQ8C_NxP2ORk5JEWvUFAYgYRQF4ve9SH2yaQjtyv_s9wOrOiMclHSN9gvc_vXpnH7Q-ZA3gE1Rz16GbHr6YJq51V9W0z8kPMUU_AoYoW1h1rraSXVmDDxKqIAl1LXQNx0CFd3uzeD-Ew6CgvF0x3MKXd0zlTmz27vOv5lmEhWkpidtf34sRIax1uK6G2Ev37rxWS0)

The green components are external services that need to be integrated.

The blue components are cloud services that will be used by the application.

The gray components are new and need to be developed

### Recommended technology stack

- NodeJs / **Typescript** ecosystem for the App Service (+**Docker**) and Print Editor (+**React**)
- Cloud alternatives:
  - AWS:
    - Route53
    - CloudFront
    - Elastic Beanstalk (for App Service)
    - S3 (for frontends)
    - Dynamo DB
    - Cognito for IDP
    - Secret Manager
  - Azure:
    - Azure AppGw
    - AppService
    - Storage (for frontends)
    - Managed DB 
    - AzureAD for IDP
    - Vault
- CI/CD
  - Github w/ **Actions**
  - **Terraform**

(highlighted are recommended team skills)

### Estimates (tshirt)

| Module | TShirt size | 
| --- | --- |
| Print Editor - frontend | XL |
| Print Editor - admin section | M |
| Print Editor - tenant whitelabel | M |
| Admin app | M |
| Tenant app | M |
| AppService | L |
| ERP Integration | L |
| Payment GW Integration| L |
| CMS | M - L |
| Identity services | M |
| DevOps | M |

Classification:

- M <10 MD (man days)
- L <50MD
- XL <150MD 
