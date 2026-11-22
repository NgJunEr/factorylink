# FactoryLink

## Software Requirements Specification (SRS)

**Project:** FactoryLink --- Global B2B Manufacturing Marketplace\
**Document type:** Software Requirements Specification\
**Version:** 1.0\
**Status:** Portfolio project baseline\
**Prepared by:** Project Owner / Software Engineering Portfolio\
**Date:** 22 November 2026

------------------------------------------------------------------------

## Document Control

  -----------------------------------------------------------------------
  Item                                Description
  ----------------------------------- -----------------------------------
  Document title                      FactoryLink Software Requirements
                                      Specification

  Product name                        FactoryLink

  Version                             1.0

  Status                              Initial baseline for design and
                                      implementation

  Intended audience                   Developers, reviewers, portfolio
                                      evaluators and project stakeholders

  Primary platforms                   Web application and mobile
                                      application

  Primary business model              B2B product discovery, supplier
                                      sourcing and custom manufacturing
                                      quotations
  -----------------------------------------------------------------------

### Version History

  Version   Date               Description
  --------- ------------------ ----------------------
  1.0       22 November 2026   Initial SRS baseline

### Approval and Change Management

This document is the initial requirements baseline for a self-directed
portfolio project. Requirements may be refined as the product is
researched, designed, implemented and tested. Any material change should
be recorded in the project change log with its rationale, impact and
approval status.

------------------------------------------------------------------------

# 1. Introduction

## 1.1 Purpose

This Software Requirements Specification (SRS) defines the business
objectives, scope, users, functional requirements, quality requirements,
system interfaces, workflows, data concepts, constraints and acceptance
criteria for FactoryLink.

The document is intended to:

-   Establish a shared understanding of the product before
    implementation.
-   Define the first deliverable version (Minimum Viable Product, or
    MVP).
-   Provide a reference for UI/UX design, database design, API
    development and testing.
-   Make project decisions and trade-offs visible to technical
    reviewers.
-   Demonstrate a structured software engineering process in a public
    portfolio.

This document describes the intended system. It does not claim that the
proposed features have already been implemented.

## 1.2 Product Overview

FactoryLink is a proposed global Business-to-Business (B2B)
manufacturing marketplace. It enables manufacturers and factories to
create business profiles, present their products and production
capabilities, and receive enquiries from business buyers.

Buyers can discover manufacturers, evaluate public company information,
browse ready-made products, and submit requests for quotation (RFQs)
when they need custom-made products or negotiated pricing.

The platform also provides administrative tools to review manufacturer
applications, moderate marketplace content and oversee platform
activity.

FactoryLink is designed around two complementary sourcing models:

1.  **Ready-made product sourcing:** A manufacturer publishes a product
    listing with specifications, minimum order quantity (MOQ),
    indicative pricing and availability information.
2.  **Custom manufacturing sourcing:** A buyer submits a description,
    specifications, quantity and supporting files. One or more
    manufacturers can respond with quotations.

The initial release is a portfolio demonstration system. It will use
synthetic company profiles, products, documents and transactions. It is
not intended to facilitate real international trade or process real
commercial payments in its MVP.

## 1.3 Business Problem

Manufacturers may have difficulty presenting their production
capabilities to a broad business audience, while buyers may find it
difficult to identify and compare suitable factories.

Common sourcing challenges include:

-   Manufacturer information is distributed across websites,
    directories, trade events and personal networks.
-   Buyers may not know which factories have the equipment or
    capabilities required for a particular job.
-   Product listings alone may not explain whether a factory accepts
    custom specifications.
-   Buyers need a structured way to communicate requirements and request
    quotations.
-   Buyers need relevant company information to support an initial
    supplier evaluation.
-   Manufacturers need a centralized place to manage product enquiries
    and quotation requests.

FactoryLink aims to provide a structured discovery and enquiry
experience. It does not guarantee that a listed company is legitimate,
that a supplier's claims are accurate, or that a transaction will be
successful. Verification labels must clearly describe the checks
actually performed by the platform.

## 1.4 Objectives

The project has the following objectives:

-   Allow manufacturers to establish profiles and present their products
    and capabilities.
-   Allow buyers to search and filter manufacturers and products.
-   Support both ready-made product enquiries and custom manufacturing
    RFQs.
-   Provide a quotation workflow between buyers and manufacturers.
-   Provide administrators with moderation and manufacturer review
    tools.
-   Provide responsive web access and a companion mobile experience.
-   Demonstrate sound database design, API design, authorization,
    testing and deployment practices.
-   Create a foundation that can later support AI-assisted discovery and
    carefully scoped blockchain-based document integrity proofs.

## 1.5 Success Criteria

The MVP will be considered successful when:

-   A manufacturer can register, complete a company profile and submit
    it for review.
-   An administrator can review and approve or reject a manufacturer
    application.
-   An approved manufacturer can publish, edit, deactivate and manage
    product listings.
-   A buyer can search and filter approved manufacturers and active
    products.
-   A buyer can submit an RFQ with structured details and optional
    attachments.
-   A manufacturer can review an RFQ and submit a quotation.
-   A buyer can view a quotation and accept or reject it.
-   Users can view the status and history of their own enquiries and
    quotations.
-   The system prevents unauthorized access to another company's private
    records.
-   Core workflows have automated tests and are documented.
-   A reviewer can run the project locally using the published setup
    instructions.

Quantitative performance targets will be established and measured during
implementation and testing rather than presented as achieved results in
advance.

## 1.6 Definitions and Abbreviations

  -----------------------------------------------------------------------
  Term                                Definition
  ----------------------------------- -----------------------------------
  B2B                                 Business-to-Business

  Manufacturer                        A registered business that produces
                                      goods or provides manufacturing
                                      services

  Buyer                               A business user searching for
                                      products or manufacturing suppliers

  RFQ                                 Request for Quotation; a buyer's
                                      structured request for price and
                                      terms

  MOQ                                 Minimum Order Quantity

  SKU                                 Stock Keeping Unit or a
                                      manufacturer's product reference

  Admin                               Authorized platform administrator

  MVP                                 Minimum Viable Product; the
                                      smallest release that demonstrates
                                      the main business workflow

  RBAC                                Role-Based Access Control

  API                                 Application Programming Interface

  UAT                                 User Acceptance Testing

  SaaS                                Software as a Service

  PII                                 Personally Identifiable Information

  Audit log                           A record of important system
                                      actions and changes
  -----------------------------------------------------------------------

## 1.7 References and Assumptions

This SRS is a project-specific planning document based on the proposed
FactoryLink concept. It is not a legal, trade compliance, security
certification or payment-processing specification.

The following assumptions apply:

-   The initial release is a portfolio demonstration, not a
    production-grade global trading service.
-   Initial data is synthetic and must not contain confidential
    employer, customer or patient information.
-   A registered account may have access to buyer and manufacturer
    capabilities if the account is associated with the appropriate
    business profile and permissions.
-   A business may have multiple staff accounts in a later release. The
    MVP may begin with one owner account per business.
-   Product prices, currencies, delivery terms, taxes and shipping
    estimates are informational in the MVP unless a later release
    explicitly implements and validates the relevant commercial rules.
-   Manufacturer verification is a platform review workflow, not a
    guarantee of legal status or product quality.
-   The platform initially uses a conventional relational database as
    the authoritative record for users, companies, products, RFQs and
    quotations.

------------------------------------------------------------------------

# 2. Overall Description

## 2.1 Product Perspective

FactoryLink is a new web and mobile application supported by a shared
backend API and relational database.

The proposed logical components are:

-   **Web application:** Public marketplace, buyer workspace,
    manufacturer workspace and administration portal.
-   **Mobile application:** Responsive task-oriented experience for
    buyers and manufacturer representatives.
-   **Backend API:** Authentication, authorization, business rules,
    marketplace operations, file metadata and notifications.
-   **Database:** Persistent storage for accounts, companies, products,
    enquiries, quotations and audit records.
-   **File storage:** Product images and RFQ attachments.
-   **External services:** Optional email, push notification, mapping,
    AI and blockchain services in later phases.

The initial architecture should be a modular monolith. Business modules
should be separated logically in the codebase without introducing
distributed services before there is a demonstrated need.

## 2.2 Product Boundaries

### Included in the MVP

-   Account registration, login and logout.
-   Buyer and manufacturer business profiles.
-   Manufacturer application review.
-   Product and capability listings.
-   Public manufacturer and product discovery.
-   Search, filtering and pagination.
-   RFQ creation and management.
-   Manufacturer quotation submission.
-   Buyer quotation review and response.
-   Basic enquiry and quotation status tracking.
-   Administrative moderation.
-   Basic in-app notifications.
-   Responsive web interface.
-   API documentation and automated tests.

### Excluded from the MVP

-   Real payment collection, escrow or fund custody.
-   Real international shipping booking and live freight rates.
-   Customs declarations, tax calculation and trade compliance
    automation.
-   Legally binding electronic signatures.
-   Automated legal or financial due diligence.
-   Guaranteed supplier identity or certification validation.
-   Full ERP, MES, WMS or accounting functionality.
-   Real-time translation of all user-generated content.
-   AI-generated supplier recommendations.
-   Blockchain-based transactions or token issuance.
-   Complex multi-tenant subscription billing.

These exclusions may be considered in future releases after the core
marketplace workflow is stable.

## 2.3 User Classes and Characteristics

  -----------------------------------------------------------------------
  User class              Description             Main capabilities
  ----------------------- ----------------------- -----------------------
  Guest                   Visitor without an      Browse public
                          authenticated account   manufacturers and
                                                  products; register or
                                                  log in

  Buyer                   Authorized              Manage buyer profile,
                          representative of a     search suppliers,
                          buyer business          submit RFQs, review
                                                  quotations

  Manufacturer owner      Owner or primary        Manage company profile,
                          representative of a     products, capabilities,
                          manufacturer account    RFQs and quotations

  Manufacturer staff      Additional employee     Perform permissions
                          account associated with assigned by the company
                          a manufacturer          owner; planned for
                                                  later release

  Platform administrator  Authorized platform     Review manufacturer
                          operator                applications, moderate
                                                  listings and manage
                                                  platform records

  Super administrator     Highly privileged       Manage administrator
                          operator                access and critical
                                                  platform configuration;
                                                  restricted operational
                                                  role
  -----------------------------------------------------------------------

A person may be associated with more than one business or business role
in a future version. The MVP should avoid assuming that a human identity
and a business organization are the same entity.

## 2.4 Operating Environment

The system is intended to support:

-   Modern desktop browsers.
-   Modern mobile browsers.
-   Android and iOS mobile devices for the companion application.
-   A backend environment capable of running the selected Laravel
    version and supporting services.
-   A PostgreSQL relational database.
-   HTTPS for all deployed environments.

Exact minimum browser and device versions will be defined during
implementation.

## 2.5 Design and Implementation Constraints

-   The backend must expose documented APIs for the web and mobile
    clients.
-   Authorization must be enforced on the server, not only by hiding UI
    controls.
-   Business data must be scoped to the relevant business and authorized
    users.
-   Uploaded files must be validated and stored outside publicly
    executable application paths.
-   Secrets and credentials must not be committed to the public
    repository.
-   The MVP must use synthetic demonstration data.
-   The system must not claim that a manufacturer is certified or
    verified unless the corresponding review process has actually been
    completed and recorded.
-   Blockchain must not be used as a replacement for ordinary relational
    data storage.
-   AI outputs must be treated as suggestions and must not silently make
    commercial decisions on behalf of users.

## 2.6 User Documentation

The public project repository should provide:

-   Main README and project overview.
-   Local development setup instructions.
-   Environment variable example file without secrets.
-   Architecture diagram.
-   Database entity relationship diagram.
-   User journey and workflow diagrams.
-   API documentation.
-   Test instructions.
-   Deployment notes.
-   Known limitations and roadmap.

------------------------------------------------------------------------

# 3. Business Process and Scope

## 3.1 Main Business Process

The core marketplace process is:

1.  A manufacturer creates an account.
2.  The manufacturer submits company information for platform review.
3.  An administrator reviews the submitted information.
4.  If approved, the manufacturer publishes products and manufacturing
    capabilities.
5.  A buyer discovers a product or manufacturer.
6.  The buyer submits an enquiry or RFQ.
7.  The manufacturer reviews the request and submits a quotation.
8.  The buyer reviews the quotation and accepts, rejects or requests
    clarification.
9.  The parties may proceed to an order workflow in a later release.

## 3.2 Primary Use Cases

  ID      Use case                          Primary actor          Release
  ------- --------------------------------- ---------------------- ---------
  UC-01   Register account                  Guest                  MVP
  UC-02   Create business profile           Buyer / Manufacturer   MVP
  UC-03   Submit manufacturer application   Manufacturer           MVP
  UC-04   Review manufacturer application   Admin                  MVP
  UC-05   Manage product listing            Manufacturer           MVP
  UC-06   Discover manufacturers            Guest / Buyer          MVP
  UC-07   Search and filter products        Guest / Buyer          MVP
  UC-08   Submit RFQ                        Buyer                  MVP
  UC-09   Review RFQ                        Manufacturer           MVP
  UC-10   Submit quotation                  Manufacturer           MVP
  UC-11   Respond to quotation              Buyer                  MVP
  UC-12   View enquiry history              Buyer / Manufacturer   MVP
  UC-13   Moderate product listing          Admin                  MVP
  UC-14   Receive notification              Authenticated user     MVP
  UC-15   Create purchase order             Buyer / Manufacturer   Later
  UC-16   Track production and shipment     Buyer / Manufacturer   Later
  UC-17   Use AI sourcing assistant         Buyer                  Later
  UC-18   Verify document integrity proof   Authorized user        Later

## 3.3 Business Rules

  -----------------------------------------------------------------------
  ID                                  Rule
  ----------------------------------- -----------------------------------
  BR-01                               Only authenticated users may
                                      perform actions that create or
                                      modify private business records.

  BR-02                               A manufacturer must have an
                                      approved manufacturer profile
                                      before publishing public product
                                      listings.

  BR-03                               A product listing must belong to
                                      one manufacturer business.

  BR-04                               A buyer cannot submit an RFQ on
                                      behalf of a business they are not
                                      authorized to represent.

  BR-05                               A manufacturer may only view and
                                      respond to RFQs addressed to that
                                      manufacturer or explicitly shared
                                      with it.

  BR-06                               A user must not submit an RFQ to
                                      their own manufacturer business.

  BR-07                               A quotation must reference an
                                      existing RFQ and the responding
                                      manufacturer must be an authorized
                                      recipient.

  BR-08                               A buyer may accept or reject only a
                                      quotation belonging to an RFQ they
                                      are authorized to manage.

  BR-09                               An accepted quotation must not be
                                      silently overwritten; later
                                      revisions must be represented as a
                                      new quotation version or amendment.

  BR-10                               Deactivation or moderation of a
                                      listing must preserve relevant
                                      historical RFQ and quotation
                                      records.

  BR-11                               Administrative actions affecting
                                      verification or moderation status
                                      must be recorded in an audit log.

  BR-12                               Public verification indicators must
                                      describe the actual scope and date
                                      of the review.

  BR-13                               Prices must include a currency code
                                      when a price is supplied.

  BR-14                               The system must not represent an
                                      indicative product price as a final
                                      binding quotation.

  BR-15                               A user may only access files
                                      associated with records they are
                                      authorized to view.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 4. Functional Requirements

## 4.1 Account and Authentication Management

**Description:** The system shall allow users to create and securely
access accounts.

  --------------------------------------------------------------------------
  ID                      Requirement                Priority
  ----------------------- -------------------------- -----------------------
  FR-AUTH-001             The system shall allow a   Must
                          guest to register using a  
                          valid email address and    
                          password.                  

  FR-AUTH-002             The system shall validate  Must
                          required registration      
                          fields and reject invalid  
                          input.                     

  FR-AUTH-003             The system shall prevent   Must
                          duplicate accounts using   
                          the same normalized email  
                          address.                   

  FR-AUTH-004             The system shall allow     Must
                          registered users to log in 
                          and log out.               

  FR-AUTH-005             The system shall provide a Must
                          secure password reset      
                          process.                   

  FR-AUTH-006             The system shall support   Should
                          email verification before  
                          enabling sensitive account 
                          actions.                   

  FR-AUTH-007             The system shall allow a   Must
                          user to view and update    
                          permitted personal account 
                          information.               

  FR-AUTH-008             The system shall allow an  Should
                          administrator to suspend   
                          an account according to    
                          platform policy.           

  FR-AUTH-009             The system shall           Must
                          invalidate or revoke       
                          authentication credentials 
                          on logout where supported  
                          by the selected            
                          authentication mechanism.  

  FR-AUTH-010             The system shall apply     Must
                          rate limits to             
                          authentication-sensitive   
                          endpoints.                 
  --------------------------------------------------------------------------

## 4.2 Business Profile Management

**Description:** The system shall represent businesses independently
from individual user accounts.

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-BIZ-001              The system shall allow  Must
                          an authorized user to   
                          create a buyer or       
                          manufacturer business   
                          profile.                

  FR-BIZ-002              A business profile      Must
                          shall include legal or  
                          display name, country,  
                          business description    
                          and contact details.    

  FR-BIZ-003              A manufacturer profile  Must
                          shall support industry  
                          categories and          
                          manufacturing           
                          capability information. 

  FR-BIZ-004              A business profile      Should
                          shall support a logo    
                          and selected gallery    
                          images.                 

  FR-BIZ-005              The system shall allow  Must
                          authorized business     
                          representatives to      
                          update permitted        
                          profile fields.         

  FR-BIZ-006              The system shall        Must
                          distinguish draft,      
                          submitted, approved,    
                          rejected and suspended  
                          manufacturer            
                          application states.     

  FR-BIZ-007              The system shall        Must
                          display only approved   
                          public manufacturer     
                          profiles in public      
                          discovery results.      

  FR-BIZ-008              The system shall record Must
                          who created and last    
                          updated a business      
                          profile.                

  FR-BIZ-009              The system shall        Should
                          support multiple users  
                          per business in a later 
                          release without         
                          redesigning the         
                          business-user           
                          relationship as a       
                          permanent one-to-one    
                          relationship.           
  -----------------------------------------------------------------------

## 4.3 Manufacturer Review and Verification

**Description:** The system shall provide a controlled administrative
review workflow.

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-VER-001              A manufacturer owner    Must
                          shall be able to submit 
                          a profile for review.   

  FR-VER-002              The system shall record Must
                          the submission date and 
                          current review status.  

  FR-VER-003              An administrator shall  Must
                          be able to view         
                          submitted manufacturer  
                          information and         
                          permitted supporting    
                          documents.              

  FR-VER-004              An administrator shall  Must
                          be able to approve or   
                          reject an application.  

  FR-VER-005              An administrator shall  Must
                          provide a reason when   
                          rejecting an            
                          application.            

  FR-VER-006              The system shall notify Should
                          the manufacturer of the 
                          review outcome.         

  FR-VER-007              The system shall record Must
                          the administrator,      
                          decision, timestamp and 
                          reason in an audit      
                          record.                 

  FR-VER-008              The platform shall      Must
                          distinguish profile     
                          review from external    
                          certification           
                          validation.             

  FR-VER-009              The system shall allow  Should
                          an approved             
                          manufacturer to submit  
                          updated information for 
                          re-review when required 
                          by platform policy.     
  -----------------------------------------------------------------------

## 4.4 Product and Manufacturing Capability Management

**Description:** The system shall allow approved manufacturers to
describe products and production capabilities.

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-PROD-001             An approved             Must
                          manufacturer shall be   
                          able to create a        
                          product listing.        

  FR-PROD-002             A product listing shall Must
                          include title,          
                          description, category   
                          and manufacturer        
                          reference.              

  FR-PROD-003             A product listing shall Must
                          support images and      
                          structured              
                          specifications.         

  FR-PROD-004             A product listing shall Must
                          support MOQ and         
                          optional indicative     
                          price range.            

  FR-PROD-005             A price range shall     Must
                          include a currency code 
                          and must be clearly     
                          identified as           
                          indicative.             

  FR-PROD-006             A product listing shall Must
                          support a status such   
                          as draft, pending       
                          review, active,         
                          inactive or rejected.   

  FR-PROD-007             A manufacturer shall be Must
                          able to edit or         
                          deactivate its own      
                          listings.               

  FR-PROD-008             The system shall        Must
                          prevent one             
                          manufacturer from       
                          modifying another       
                          manufacturer's          
                          listings.               

  FR-PROD-009             The system shall allow  Should
                          manufacturers to add    
                          capability information  
                          such as process type,   
                          material, equipment or  
                          production range.       

  FR-PROD-010             The system shall allow  Must
                          administrators to       
                          moderate reported or    
                          non-compliant listings. 

  FR-PROD-011             Public search shall     Must
                          return only active      
                          listings from approved  
                          manufacturers.          

  FR-PROD-012             The system shall        Must
                          preserve references to  
                          products used in        
                          historical RFQs even if 
                          a listing is later      
                          deactivated.            
  -----------------------------------------------------------------------

## 4.5 Manufacturer and Product Discovery

**Description:** The system shall help guests and buyers discover
relevant suppliers and products.

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-SRCH-001             The system shall        Must
                          provide public          
                          manufacturer browsing.  

  FR-SRCH-002             The system shall        Must
                          provide public product  
                          browsing.               

  FR-SRCH-003             Users shall be able to  Must
                          search products by      
                          keyword.                

  FR-SRCH-004             Users shall be able to  Must
                          filter products by      
                          category and            
                          manufacturer country.   

  FR-SRCH-005             Users shall be able to  Should
                          filter manufacturers by 
                          country and industry.   

  FR-SRCH-006             Search results shall    Must
                          support pagination.     

  FR-SRCH-007             Search results shall    Must
                          provide a product or    
                          manufacturer detail     
                          view.                   

  FR-SRCH-008             Search shall not expose Must
                          private manufacturer    
                          documents or private    
                          contact information.    

  FR-SRCH-009             The system should       Should
                          provide sorting by      
                          relevance and recently  
                          added listings.         

  FR-SRCH-010             Empty search results    Should
                          shall provide a clear   
                          message and allow the   
                          user to revise filters. 
  -----------------------------------------------------------------------

## 4.6 Request for Quotation (RFQ)

**Description:** The system shall support structured enquiries for
ready-made and custom-manufactured products.

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-RFQ-001              An authenticated buyer  Must
                          shall be able to create 
                          an RFQ.                 

  FR-RFQ-002              An RFQ shall identify   Must
                          the buyer business and  
                          the authorized          
                          submitting user.        

  FR-RFQ-003              An RFQ shall include    Must
                          title, description,     
                          requested quantity and  
                          target delivery         
                          information where       
                          known.                  

  FR-RFQ-004              An RFQ shall support an Must
                          optional reference to   
                          an existing product     
                          listing.                

  FR-RFQ-005              An RFQ shall support    Must
                          custom manufacturing    
                          specifications.         

  FR-RFQ-006              An RFQ shall support    Must
                          optional attachments    
                          subject to file         
                          validation rules.       

  FR-RFQ-007              A buyer shall be able   Must
                          to direct an RFQ to a   
                          selected manufacturer.  

  FR-RFQ-008              The system shall        Must
                          prevent a buyer from    
                          sending an RFQ to a     
                          manufacturer business   
                          they control.           

  FR-RFQ-009              The buyer shall be able Must
                          to view the RFQs        
                          belonging to their      
                          authorized business.    

  FR-RFQ-010              The buyer shall be able Should
                          to cancel an RFQ before 
                          it reaches a locked or  
                          completed state,        
                          subject to workflow     
                          rules.                  

  FR-RFQ-011              The system shall record Must
                          RFQ creation and status 
                          changes.                

  FR-RFQ-012              The system shall        Must
                          prevent unauthorized    
                          users from viewing      
                          private RFQ details and 
                          attachments.            
  -----------------------------------------------------------------------

## 4.7 Quotation Management

**Description:** The system shall allow a manufacturer to respond to an
RFQ with a structured quotation.

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-QUO-001              An authorized           Must
                          manufacturer            
                          representative shall be 
                          able to view RFQs       
                          addressed to their      
                          business.               

  FR-QUO-002              An authorized           Must
                          manufacturer            
                          representative shall be 
                          able to submit a        
                          quotation for an        
                          eligible RFQ.           

  FR-QUO-003              A quotation shall       Must
                          include unit price,     
                          currency, quantity,     
                          validity date and       
                          estimated lead time.    

  FR-QUO-004              A quotation shall       Should
                          support optional notes, 
                          exclusions and terms.   

  FR-QUO-005              The system shall        Must
                          calculate and display a 
                          quotation subtotal      
                          using validated         
                          quantity and unit price 
                          values.                 

  FR-QUO-006              The system shall        Must
                          identify the            
                          manufacturer and RFQ    
                          associated with each    
                          quotation.              

  FR-QUO-007              A manufacturer shall be Must
                          able to view quotations 
                          submitted by its own    
                          business.               

  FR-QUO-008              A buyer shall be able   Must
                          to view quotations      
                          received for its RFQs.  

  FR-QUO-009              A buyer shall be able   Must
                          to accept or reject an  
                          eligible quotation.     

  FR-QUO-010              The system shall        Must
                          preserve quotation      
                          history and prevent     
                          silent overwriting of   
                          previously submitted    
                          quotations.             

  FR-QUO-011              The system shall record Must
                          the user and timestamp  
                          for quotation           
                          submission and buyer    
                          response.               

  FR-QUO-012              A quotation shall not   Must
                          be represented as a     
                          paid order unless a     
                          separate order and      
                          payment workflow has    
                          been implemented.       
  -----------------------------------------------------------------------

## 4.8 Order Management --- Later Release

The MVP may stop at quotation acceptance. The following requirements
define a future extension and are not required for the initial release.

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-ORD-001              The system should allow Later
                          an accepted quotation   
                          to be converted into an 
                          order.                  

  FR-ORD-002              An order should         Later
                          preserve a snapshot of  
                          the agreed quotation    
                          terms.                  

  FR-ORD-003              The system should       Later
                          support order statuses  
                          such as confirmed, in   
                          production, quality     
                          check, ready for        
                          dispatch, shipped,      
                          delivered and           
                          cancelled.              

  FR-ORD-004              Authorized parties      Later
                          should be able to view  
                          order status and status 
                          history.                

  FR-ORD-005              The system should       Later
                          record the user and     
                          timestamp for each      
                          order status change.    

  FR-ORD-006              The system should       Later
                          support shipment        
                          references and document 
                          attachments.            
  -----------------------------------------------------------------------

## 4.9 Notifications

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-NOTI-001             The system shall create Must
                          an in-app notification  
                          when a relevant RFQ is  
                          received.               

  FR-NOTI-002             The system shall create Must
                          an in-app notification  
                          when a quotation is     
                          submitted.              

  FR-NOTI-003             The system shall notify Should
                          a manufacturer when its 
                          application review is   
                          completed.              

  FR-NOTI-004             A user shall be able to Must
                          view and mark their     
                          notifications as read.  

  FR-NOTI-005             The system should       Should
                          support email           
                          notifications for       
                          important workflow      
                          events.                 

  FR-NOTI-006             The system may support  Later
                          mobile push             
                          notifications in the    
                          mobile release.         
  -----------------------------------------------------------------------

## 4.10 Administration and Moderation

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-ADMIN-001            An administrator shall  Must
                          be able to access an    
                          administrative          
                          dashboard.              

  FR-ADMIN-002            An administrator shall  Must
                          be able to search and   
                          view user and business  
                          records according to    
                          assigned permissions.   

  FR-ADMIN-003            An administrator shall  Must
                          be able to review       
                          manufacturer            
                          applications.           

  FR-ADMIN-004            An administrator shall  Must
                          be able to approve,     
                          reject or suspend       
                          eligible listings.      

  FR-ADMIN-005            An administrator shall  Should
                          be able to suspend an   
                          account according to    
                          platform policy.        

  FR-ADMIN-006            The dashboard shall     Should
                          display basic counts    
                          for users,              
                          manufacturers, products 
                          and RFQs.               

  FR-ADMIN-007            The system shall record Must
                          privileged              
                          administrative actions  
                          in an audit log.        

  FR-ADMIN-008            Administrative access   Must
                          shall be restricted to  
                          authorized              
                          administrator accounts. 
  -----------------------------------------------------------------------

## 4.11 Mobile Application

The mobile application shall use the same backend business rules and
authorization controls as the web application.

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-MOB-001              A user shall be able to Should
                          authenticate through    
                          the mobile application. 

  FR-MOB-002              A buyer shall be able   Should
                          to view their RFQs and  
                          quotation updates.      

  FR-MOB-003              A manufacturer          Should
                          representative shall be 
                          able to view incoming   
                          RFQs.                   

  FR-MOB-004              An authorized           Should
                          manufacturer            
                          representative shall be 
                          able to submit or       
                          update a quotation      
                          where permitted.        

  FR-MOB-005              A user shall be able to Later
                          receive push            
                          notifications where     
                          device permissions and  
                          notification services   
                          are available.          

  FR-MOB-006              The mobile application  Must
                          shall provide           
                          appropriate loading,    
                          error, empty and        
                          offline states.         

  FR-MOB-007              The mobile application  Must
                          shall not store         
                          sensitive business      
                          files in an unprotected 
                          public location.        
  -----------------------------------------------------------------------

## 4.12 AI Features --- Future Release

Potential AI capabilities include:

-   Natural-language search for manufacturers and products.
-   Extraction of product specifications from buyer-provided documents.
-   Summaries of manufacturer capabilities based on published profile
    information.
-   Comparison of quotation fields in a structured, explainable format.
-   Drafting assistance for RFQ descriptions.

AI requirements for a future release:

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-AI-001               The system may convert  Later
                          a natural-language      
                          query into suggested    
                          marketplace filters.    

  FR-AI-002               The system may extract  Later
                          candidate fields from   
                          an uploaded             
                          specification document  
                          for user review.        

  FR-AI-003               The system shall        Later
                          identify AI-generated   
                          content as a            
                          suggestion.             

  FR-AI-004               The system shall        Later
                          require user            
                          confirmation before an  
                          AI suggestion is        
                          submitted as an RFQ or  
                          quotation.              

  FR-AI-005               The system shall not    Later
                          expose private business 
                          data to an AI provider  
                          without an explicitly   
                          designed and disclosed  
                          data-processing flow.   

  FR-AI-006               The system shall        Later
                          provide a fallback path 
                          when an AI service is   
                          unavailable.            
  -----------------------------------------------------------------------

## 4.13 Web3 Features --- Future Release

Potential Web3 capabilities should be narrowly scoped to verifiable
evidence rather than replacing the marketplace database.

Possible use cases:

-   Record a cryptographic hash of a finalized document.
-   Verify that a later document matches a previously recorded hash.
-   Record a proof that an approval event occurred at a particular time.
-   Allow a user to connect a compatible wallet for an optional
    verification action.

  -----------------------------------------------------------------------
  ID                      Requirement             Priority
  ----------------------- ----------------------- -----------------------
  FR-WEB3-001             The system may generate Later
                          a cryptographic hash    
                          for a finalized         
                          document.               

  FR-WEB3-002             The system may submit   Later
                          the hash and a          
                          non-sensitive reference 
                          to a supported          
                          blockchain network.     

  FR-WEB3-003             The system shall keep   Later
                          personal information,   
                          confidential            
                          specifications and full 
                          business documents      
                          off-chain.              

  FR-WEB3-004             The system shall        Later
                          explain that a matching 
                          hash demonstrates       
                          integrity relative to a 
                          recorded hash, not the  
                          truth or legal validity 
                          of the document.        

  FR-WEB3-005             Blockchain interaction  Later
                          shall be optional and   
                          shall not prevent       
                          normal marketplace      
                          usage.                  

  FR-WEB3-006             Smart contracts shall   Later
                          be tested and reviewed  
                          before any deployment   
                          beyond a test network.  
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 5. External Interface Requirements

## 5.1 User Interface

The user interface shall:

-   Provide a consistent navigation structure across public, buyer,
    manufacturer and admin areas.
-   Clearly distinguish public information from private business
    workspaces.
-   Display validation errors near the relevant fields.
-   Provide confirmation for important actions such as rejecting a
    quotation or deactivating a listing.
-   Provide loading, empty, success and error states.
-   Use responsive layouts for desktop, tablet and mobile browser sizes.
-   Use accessible labels and keyboard-operable controls where
    practical.
-   Clearly label indicative prices, review statuses and verification
    scope.

## 5.2 Software Interfaces

  -----------------------------------------------------------------------
  Interface               Purpose                 Initial approach
  ----------------------- ----------------------- -----------------------
  Web client to backend   Marketplace and         HTTPS REST API
                          workspace operations    

  Mobile client to        Mobile workflow         Same HTTPS REST API
  backend                 operations              

  Backend to PostgreSQL   Persistent relational   Database driver / ORM
                          data                    

  Backend to file storage Images and attachments  Private object or
                                                  filesystem storage

  Backend to email        Account and workflow    Provider adapter
  provider                email                   

  Backend to push         Mobile push             Later integration
  provider                notifications           

  Backend to AI service   AI-assisted discovery   Later service/API
                          and document extraction integration

  Backend to blockchain   Hash and proof          Later contract
                          registration            integration
  -----------------------------------------------------------------------

## 5.3 API Design Principles

-   Use resource-oriented REST endpoints.
-   Use consistent HTTP status codes.
-   Validate all input on the server.
-   Return consistent success and error response structures.
-   Apply authentication and authorization to private endpoints.
-   Support pagination for collection endpoints.
-   Avoid exposing internal database implementation details.
-   Version the API when breaking changes are introduced.
-   Document request parameters, response schemas, authorization rules
    and error cases.

### Illustrative API Resource Map

These are proposed endpoint examples, not implemented endpoints.

  -------------------------------------------------------------------------------------------
  Method                  Example endpoint                            Purpose
  ----------------------- ------------------------------------------- -----------------------
  POST                    `/api/v1/auth/register`                     Register account

  POST                    `/api/v1/auth/login`                        Authenticate

  POST                    `/api/v1/auth/logout`                       End authenticated
                                                                      session

  GET                     `/api/v1/manufacturers`                     Browse approved
                                                                      manufacturers

  GET                     `/api/v1/manufacturers/{id}`                View public
                                                                      manufacturer profile

  POST                    `/api/v1/businesses`                        Create business profile

  POST                    `/api/v1/manufacturer-applications`         Submit manufacturer
                                                                      application

  POST                    `/api/v1/products`                          Create product listing

  GET                     `/api/v1/products`                          Search and browse
                                                                      products

  GET                     `/api/v1/products/{id}`                     View product detail

  POST                    `/api/v1/rfqs`                              Create RFQ

  GET                     `/api/v1/rfqs`                              List authorized RFQs

  GET                     `/api/v1/rfqs/{id}`                         View authorized RFQ

  POST                    `/api/v1/rfqs/{id}/quotations`              Submit quotation

  GET                     `/api/v1/quotations/{id}`                   View authorized
                                                                      quotation

  POST                    `/api/v1/quotations/{id}/accept`            Accept quotation

  POST                    `/api/v1/quotations/{id}/reject`            Reject quotation

  GET                     `/api/v1/notifications`                     List user notifications

  PATCH                   `/api/v1/notifications/{id}/read`           Mark notification as
                                                                      read

  GET                     `/api/v1/admin/manufacturer-applications`   Admin review queue
  -------------------------------------------------------------------------------------------

------------------------------------------------------------------------

# 6. Data Requirements and Conceptual Model

## 6.1 Data Design Principles

-   Individual user accounts and business organizations shall be
    separate concepts.
-   A business may have multiple users in a future release.
-   Every private business record shall have a clear ownership or access
    scope.
-   Important business workflow changes shall be timestamped.
-   Historical commercial records shall remain understandable if a
    product or profile changes later.
-   Files shall be represented by metadata records and stored through a
    controlled storage service.
-   Monetary values shall use appropriate decimal precision and an
    explicit currency code.
-   Database constraints and transactions shall protect important
    relationships and state changes.

## 6.2 Conceptual Entities

  -----------------------------------------------------------------------------
  Entity                    Purpose                 Example attributes
  ------------------------- ----------------------- ---------------------------
  User                      Individual account      id, name, email,
                                                    password_hash, status

  Business                  Organization using the  id, business_name,
                            platform                country_code, description,
                                                    status

  BusinessUser              Membership linking      id, business_id, user_id,
                            users and businesses    role, status

  ManufacturerProfile       Manufacturer-specific   business_id, review_status,
                            information             industry,
                                                    capabilities_summary

  BuyerProfile              Buyer-specific          business_id,
                            information             purchasing_categories

  ManufacturerApplication   Review submission and   id, business_id,
                            decision                submitted_at, decision,
                                                    reviewer_id

  Industry                  Industry classification id, name, parent_id

  ProductCategory           Product classification  id, name, parent_id

  Product                   Published product or    id, business_id,
                            offering                category_id, title,
                                                    description, status

  ProductImage              Product image metadata  id, product_id,
                                                    storage_key, sort_order

  ProductSpecification      Structured product      id, product_id,
                            attributes              attribute_name,
                                                    attribute_value

  ManufacturingCapability   Factory process or      id, business_id,
                            capability              capability_type,
                                                    description

  RFQ                       Buyer sourcing request  id, buyer_business_id,
                                                    created_by, status,
                                                    due_date

  RFQRecipient              Manufacturer invited to id, rfq_id,
                            respond                 manufacturer_business_id,
                                                    response_status

  RFQItem                   Requested product or    id, rfq_id, description,
                            specification           quantity, unit

  RFQAttachment             Private RFQ file        id, rfq_id, storage_key,
                            metadata                original_name

  Quotation                 Manufacturer's          id, rfq_id,
                            commercial response     manufacturer_business_id,
                                                    version, status

  QuotationItem             Quoted line item        id, quotation_id,
                                                    description, quantity,
                                                    unit_price, currency

  Notification              User-facing event       id, user_id, type, payload,
                            notification            read_at

  AuditLog                  Important system        id, actor_id, action,
                            activity                entity_type, entity_id,
                                                    created_at

  FileAsset                 Controlled file         id, owner_business_id,
                            metadata                storage_key, mime_type,
                                                    size
  -----------------------------------------------------------------------------

This is a conceptual model. The final physical schema, normalization,
indexes and constraints must be confirmed during database design.

## 6.3 Key Relationships

-   One user may belong to many businesses through BusinessUser.
-   One business may have many users through BusinessUser.
-   A manufacturer business may have one manufacturer profile.
-   A business may publish many products.
-   A product may have many images and specifications.
-   A buyer business may create many RFQs.
-   An RFQ may contain many RFQ items and attachments.
-   An RFQ may be sent to one or more manufacturer businesses through
    RFQRecipient.
-   An RFQ may receive multiple quotations, subject to recipient and
    workflow rules.
-   A quotation may contain multiple quotation items.
-   A user may receive many notifications.
-   An audit log entry references the actor and the affected entity.

## 6.4 Data Retention and Deletion

-   Account deletion must consider business ownership and historical
    commercial records.
-   Historical RFQs and quotations should not be destroyed merely
    because a product listing is deactivated.
-   Files should be removed or retained according to a documented
    retention policy.
-   Audit records should be protected against ordinary user
    modification.
-   The portfolio demonstration should use synthetic data and should
    provide a reset or seed process.

------------------------------------------------------------------------

# 7. Non-Functional Requirements

The following requirements describe quality attributes. Where a numeric
threshold is not yet established, the implementation team shall define
and measure an appropriate target during testing.

## 7.1 Security

  -----------------------------------------------------------------------
  ID                                  Requirement
  ----------------------------------- -----------------------------------
  NFR-SEC-001                         All deployed application traffic
                                      shall use HTTPS.

  NFR-SEC-002                         Passwords shall be stored using a
                                      modern adaptive password hashing
                                      mechanism supported by the
                                      framework.

  NFR-SEC-003                         The backend shall enforce
                                      authorization for every private
                                      business resource.

  NFR-SEC-004                         The system shall validate and
                                      sanitize untrusted input using
                                      context-appropriate controls.

  NFR-SEC-005                         File uploads shall enforce allowed
                                      file types, size limits and safe
                                      storage rules.

  NFR-SEC-006                         Secrets, private keys and
                                      production credentials shall not be
                                      committed to source control.

  NFR-SEC-007                         Authentication and sensitive
                                      endpoints shall be rate-limited.

  NFR-SEC-008                         Administrative actions and
                                      important workflow changes shall be
                                      auditable.

  NFR-SEC-009                         The system shall protect against
                                      common web application risks,
                                      including injection, broken access
                                      control and cross-site scripting.

  NFR-SEC-010                         The system shall avoid exposing
                                      private contact details, documents
                                      or RFQ data through public
                                      endpoints.
  -----------------------------------------------------------------------

## 7.2 Performance

-   Public listing endpoints shall use pagination.
-   Search and filtering shall use appropriate database indexes.
-   Large images shall be resized or optimized where appropriate.
-   Expensive operations should be moved to background jobs when
    justified.
-   The project shall define response-time targets and validate them
    with repeatable tests.
-   Performance claims in portfolio materials shall be supported by
    measured test results.

## 7.3 Availability and Reliability

-   The application shall return understandable errors when a dependent
    service is unavailable.
-   Important state changes shall use database transactions where
    multiple records must remain consistent.
-   Background jobs shall support retry and failure handling.
-   The deployment plan shall document backup and restore procedures.
-   External integrations shall not be allowed to corrupt core
    marketplace records when unavailable.

## 7.4 Usability and Accessibility

-   Main workflows shall be understandable without technical knowledge.
-   Forms shall provide clear labels, required-field indicators and
    validation messages.
-   Status values shall use consistent names and visual treatments.
-   The interface shall support common screen sizes.
-   Interactive controls shall have accessible names and keyboard
    support where practical.
-   Destructive actions shall require confirmation.

## 7.5 Maintainability

-   Code shall be organized by clear business modules or domains.
-   Business rules shall not exist only in frontend components.
-   Shared API response conventions shall be documented.
-   Automated tests shall cover critical authorization and transaction
    workflows.
-   Configuration shall be environment-driven.
-   Significant architecture decisions shall be recorded as Architecture
    Decision Records (ADRs).

## 7.6 Scalability

-   The initial system shall use a modular monolith.
-   Data access patterns shall be reviewed before adding caching or
    service separation.
-   Business and user relationships shall support future multiple-user
    organizations.
-   Background job processing shall be available for asynchronous
    workloads.
-   Microservices shall only be considered when independently deployable
    scaling or ownership needs justify their operational cost.

## 7.7 Compatibility

-   The web application shall support current mainstream desktop and
    mobile browsers.
-   The mobile application shall target supported Android and iOS
    versions selected during implementation.
-   API clients shall use documented, stable response contracts.

## 7.8 Privacy

-   Only data necessary for the marketplace workflow shall be collected.
-   Public profile fields shall be separated from private business and
    user information.
-   Private RFQ attachments shall require authorization.
-   Synthetic data shall be used in public demos.
-   The project shall document any third-party services that receive
    user-submitted data.
-   The portfolio version shall not use real employer or customer
    information.

------------------------------------------------------------------------

# 8. System Architecture

## 8.1 Proposed Technology Stack

  -----------------------------------------------------------------------
  Layer                   Proposed technology     Responsibility
  ----------------------- ----------------------- -----------------------
  Web frontend            Next.js, TypeScript     Public marketplace and
                                                  business workspaces

  Mobile frontend         React Native, Expo      Mobile buyer and
                                                  manufacturer workflows

  Backend                 Laravel REST API        Business rules,
                                                  authentication and API
                                                  services

  Database                PostgreSQL              Authoritative
                                                  relational data store

  Cache and queues        Redis                   Cache and asynchronous
                                                  job support

  File storage            Local private storage   Images and attachments
                          for development; object 
                          storage for deployment  

  API testing             Postman                 Manual API verification

  Backend testing         Pest or PHPUnit         Automated backend tests

  Web testing             Vitest and              Frontend tests
                          browser-level testing   
                          tools                   

  Containerization        Docker                  Reproducible
                                                  development and
                                                  deployment

  CI/CD                   GitHub Actions          Automated quality
                                                  checks and deployment
                                                  workflow

  AI service              Python/FastAPI, future  Isolated AI
                          phase                   capabilities

  Blockchain              Solidity and Foundry,   Optional document
                          future phase            integrity proofs
  -----------------------------------------------------------------------

Technology versions shall be selected and pinned when implementation
begins. This document does not mandate unverified version numbers.

## 8.2 Logical Architecture

``` mermaid
flowchart TB
    Guest[Guest / Buyer / Manufacturer / Admin]
    Web[Next.js Web Application]
    Mobile[React Native Mobile Application]
    API[Laravel REST API]
    Auth[Identity and Authorization]
    Modules[Marketplace Modules]
    DB[(PostgreSQL)]
    Redis[(Redis Cache / Queue)]
    Files[Private File Storage]
    Mail[Email / Push Providers]
    AI[Future AI Service]
    Chain[Future Blockchain Network]

    Guest --> Web
    Guest --> Mobile
    Web --> API
    Mobile --> API
    API --> Auth
    API --> Modules
    Modules --> DB
    API --> Redis
    Modules --> Files
    API --> Mail
    Modules -. Future integration .-> AI
    Modules -. Optional proof integration .-> Chain
```

## 8.3 Proposed Backend Modules

-   Identity and Access
-   Business and Membership
-   Manufacturer Review
-   Product Catalogue
-   Manufacturing Capabilities
-   Search and Discovery
-   RFQ Management
-   Quotation Management
-   Notifications
-   Administration and Audit

## 8.4 Architecture Principles

-   Keep the backend as the authoritative source of business rules.
-   Keep web and mobile clients independent of database implementation
    details.
-   Separate business organizations from individual accounts.
-   Enforce business-level authorization at the API boundary and within
    application services.
-   Use transactions for state transitions that affect related records.
-   Keep optional AI and blockchain integrations isolated behind service
    interfaces.
-   Avoid premature microservices and unnecessary infrastructure.

------------------------------------------------------------------------

# 9. Core Workflow Specifications

## 9.1 Manufacturer Onboarding

**Primary actor:** Manufacturer owner\
**Supporting actor:** Platform administrator

**Preconditions:** - The user has a registered account. - The user is
authenticated.

**Main flow:** 1. The user creates a manufacturer business profile. 2.
The user enters company information, country, industry and capabilities.
3. The user uploads permitted supporting documents if required by the
configured review policy. 4. The user submits the application. 5. The
system validates required information and records the submission. 6. The
application appears in the administrator review queue. 7. The
administrator reviews the application. 8. The administrator approves or
rejects it with a reason. 9. The system records the decision and
notifies the manufacturer. 10. If approved, the manufacturer may publish
product listings.

**Alternative flows:** - If required fields are missing, the system
displays validation errors. - If rejected, the manufacturer may correct
the information and resubmit according to platform policy. - If
suspended, public listings are hidden or restricted according to
moderation rules.

**Postconditions:** - The application has a recorded status and review
history. - Public manufacturer visibility reflects the current approved
status.

## 9.2 Product Publication

**Primary actor:** Manufacturer representative

**Preconditions:** - The user is authorized for the manufacturer
business. - The manufacturer is approved.

**Main flow:** 1. The user opens product management. 2. The user creates
a product draft. 3. The user enters product title, description,
category, specifications, MOQ and optional indicative price. 4. The user
uploads product images. 5. The user saves the draft or submits it for
publication. 6. The system validates the listing. 7. The listing becomes
active immediately or after moderation, depending on platform policy. 8.
The listing appears in public discovery when active and eligible.

**Postconditions:** - The product is stored with its manufacturer
ownership. - The public catalogue reflects its permitted status.

## 9.3 Buyer RFQ Submission

**Primary actor:** Buyer representative

**Preconditions:** - The user is authenticated. - The user is authorized
for a buyer business.

**Main flow:** 1. The buyer browses a product or manufacturer profile.
2. The buyer selects the option to request a quotation. 3. The buyer
enters quantity, specifications, target delivery information and notes.
4. The buyer selects the intended manufacturer. 5. The buyer attaches
relevant documents if needed. 6. The system validates the RFQ and
verifies that the buyer is not submitting it to its own manufacturer
business. 7. The system creates the RFQ and recipient record. 8. The
manufacturer receives a notification.

**Alternative flows:** - If the buyer is not authorized for the
business, submission is rejected. - If an attachment fails validation,
the system rejects that file and explains the reason. - If the selected
manufacturer is inactive or not eligible, the system prevents
submission.

**Postconditions:** - The RFQ is stored and visible only to authorized
parties.

## 9.4 Manufacturer Quotation Response

**Primary actor:** Manufacturer representative

**Preconditions:** - The RFQ is addressed to the manufacturer's
business. - The user is authorized for that business. - The RFQ is in a
state that accepts responses.

**Main flow:** 1. The manufacturer opens the RFQ. 2. The manufacturer
reviews specifications and attachments. 3. The manufacturer enters
price, currency, quantity, lead time and validity date. 4. The
manufacturer adds optional terms or notes. 5. The system validates the
quotation. 6. The system creates a quotation version. 7. The buyer
receives a notification.

**Postconditions:** - The quotation is linked to the RFQ and
manufacturer. - The quotation is visible to the buyer and authorized
manufacturer users.

## 9.5 Buyer Quotation Decision

**Primary actor:** Buyer representative

**Preconditions:** - The quotation belongs to an RFQ managed by the
buyer's business. - The quotation is awaiting a buyer decision.

**Main flow:** 1. The buyer opens the quotation. 2. The buyer reviews
the price, currency, quantity, validity and terms. 3. The buyer accepts
or rejects the quotation. 4. The system validates the current quotation
state. 5. The system records the decision, actor and timestamp. 6. The
manufacturer receives a notification.

**Postconditions:** - The quotation status reflects the buyer's
decision. - The decision history is retained. - Acceptance does not
imply payment, shipment or legal execution unless those features are
separately implemented.

------------------------------------------------------------------------

# 10. Status Models

## 10.1 Manufacturer Application

Proposed statuses:

``` text
DRAFT
  |
  v
SUBMITTED ---> REJECTED
  |                |
  v                v
APPROVED <----- RESUBMITTED
  |
  v
SUSPENDED (administrative action)
```

The implementation shall define permitted transitions explicitly. A
rejected application must not become approved without a new review
decision.

## 10.2 Product Listing

Proposed statuses:

-   Draft
-   Pending Review
-   Active
-   Inactive
-   Rejected
-   Suspended

Only active listings from approved manufacturers are eligible for public
discovery.

## 10.3 RFQ

Proposed statuses:

-   Draft
-   Submitted
-   Sent to Manufacturer
-   Response Received
-   Under Discussion
-   Closed
-   Cancelled

The final state model may be refined to distinguish the RFQ's overall
status from each manufacturer's individual response status.

## 10.4 Quotation

Proposed statuses:

-   Draft
-   Submitted
-   Revised
-   Accepted
-   Rejected
-   Expired
-   Withdrawn

Quotation versioning and transition rules shall be enforced by the
backend.

------------------------------------------------------------------------

# 11. Testing and Acceptance

## 11.1 Testing Strategy

  -----------------------------------------------------------------------
  Test level              Purpose                 Examples
  ----------------------- ----------------------- -----------------------
  Unit testing            Verify isolated         Price calculations,
                          business rules          status transition rules

  Feature/API testing     Verify endpoint         Registration, product
                          behavior                creation, RFQ
                                                  submission

  Authorization testing   Verify access           Buyer cannot view
                          boundaries              another buyer's RFQ

  Integration testing     Verify connected        Database transaction
                          components              and notification
                                                  creation

  UI testing              Verify important user   Search, profile, RFQ
                          journeys                and quotation screens

  Mobile testing          Verify mobile-specific  Authentication, offline
                          behavior                state and push
                                                  permissions

  Security testing        Identify common         Access control,
                          vulnerabilities         validation, file upload
                                                  handling

  UAT                     Confirm workflows meet  Manufacturer onboarding
                          intended requirements   and buyer quotation
                                                  flow
  -----------------------------------------------------------------------

## 11.2 Minimum Acceptance Scenarios

  -----------------------------------------------------------------------
  ID                      Scenario                Expected result
  ----------------------- ----------------------- -----------------------
  AT-001                  Register with valid     Account is created
                          information             

  AT-002                  Register with an        Registration is
                          existing email          rejected with a clear
                                                  validation message

  AT-003                  Unapproved manufacturer Publication is denied
                          attempts to publish a   
                          product                 

  AT-004                  Approved manufacturer   Product is saved and
                          creates a valid product can become active

  AT-005                  Buyer searches for an   Matching eligible
                          active product          products are returned

  AT-006                  Buyer submits a valid   RFQ is created and
                          RFQ                     recipient is notified

  AT-007                  Buyer attempts to send  Request is rejected
                          an RFQ to its own       
                          manufacturer business   

  AT-008                  Unrelated manufacturer  Access is denied
                          requests a private RFQ  

  AT-009                  Intended manufacturer   Quotation is created
                          submits a valid         
                          quotation               

  AT-010                  Buyer accepts an        Decision is recorded
                          eligible quotation      

  AT-011                  User attempts to modify Access is denied
                          another business's      
                          product                 

  AT-012                  Administrator rejects a Action is rejected if a
                          manufacturer            reason is required
                          application without a   
                          reason                  

  AT-013                  User attempts to        Access is denied
                          download an             
                          unauthorized RFQ        
                          attachment              

  AT-014                  Product is deactivated  Historical RFQ remains
                          after being referenced  readable to authorized
                          by an RFQ               parties

  AT-015                  A notification is       Read state is updated
                          marked as read          for the authorized user
  -----------------------------------------------------------------------

## 11.3 Definition of Done

A feature is not complete merely because its screen exists. A feature
should be considered complete when:

-   Requirements and expected behavior are documented.
-   Validation and authorization are implemented server-side.
-   Relevant success and failure states are handled.
-   Database constraints and transactions are considered.
-   Automated tests cover important behavior.
-   API documentation is updated.
-   The UI is usable at supported screen sizes.
-   No secrets or real private data are committed.
-   The change is reviewed and documented in Git.

------------------------------------------------------------------------

# 12. Deployment and Operations

## 12.1 Environments

The project should distinguish:

-   **Local development:** Developer machine and synthetic seed data.
-   **Test/staging:** Deployed environment for integration and UAT.
-   **Demo/production-like:** Public portfolio demonstration with
    synthetic data and restricted administrative access.

## 12.2 Deployment Requirements

-   Use environment variables for configuration.
-   Use HTTPS in deployed environments.
-   Use a managed or properly secured PostgreSQL instance.
-   Configure private file storage and access controls.
-   Configure background workers if queues are used.
-   Configure scheduled tasks only where required.
-   Run database migrations through a controlled deployment process.
-   Provide a backup and restore procedure.
-   Keep application logs free of passwords, tokens and sensitive file
    contents.
-   Restrict access to administrative accounts.

## 12.3 CI/CD Baseline

A GitHub Actions workflow should progressively automate:

1.  Dependency installation.
2.  Code formatting or lint checks.
3.  Backend static checks where configured.
4.  Backend automated tests.
5.  Frontend lint and test commands.
6.  Build verification.
7.  Deployment after required checks and approvals.

The initial project may deploy manually. Automated deployment can be
introduced after repeatable build and test steps are established.

## 12.4 Monitoring

For the public demo, monitor at least:

-   Application availability.
-   Application error logs.
-   Failed background jobs.
-   Database connectivity.
-   Storage failures.
-   Unexpected authentication or authorization errors.

Do not publish private logs or operational credentials in the portfolio
repository.

------------------------------------------------------------------------

# 13. Risks and Mitigations

  ------------------------------------------------------------------------
  Risk                    Potential impact        Mitigation
  ----------------------- ----------------------- ------------------------
  Scope becomes too large MVP is never completed  Prioritize the core
                                                  discovery-to-quotation
                                                  workflow

  Project resembles a     Limited differentiation Emphasize manufacturing
  generic marketplace                             capabilities and custom
                                                  RFQs

  Weak business           Private company data    Model business
  authorization           exposure                membership and test
                                                  cross-business access

  Fake or misleading      Loss of trust           Define exact review
  verification claims                             scope and display
                                                  precise status labels

  Complex global trade    Excessive               Exclude payments,
  requirements            implementation effort   customs and shipping
                                                  automation from MVP

  AI produces incorrect   Poor sourcing decisions Require user review and
  suggestions                                     confirmation

  Blockchain adds         More development and    Limit it to optional
  complexity without      maintenance             integrity proofs with a
  value                                           clear use case

  File uploads create     Malware or data leakage Validate, restrict,
  security exposure                               store privately and
                                                  authorize downloads

  Deployment              Demo downtime or data   Document environment
  configuration errors    loss                    setup, backups and
                                                  deployment checks

  Use of confidential     Privacy and legal risk  Use synthetic data and
  real-world data                                 fictional organizations
  ------------------------------------------------------------------------

------------------------------------------------------------------------

# 14. Project Roadmap

The roadmap is incremental. Completion dates should be assigned after
estimating the work and considering available development time.

## Release 0 --- Research and Planning

-   Review existing B2B manufacturing marketplaces.
-   Identify common buyer and manufacturer journeys.
-   Define product categories and capability taxonomy.
-   Finalize SRS and MVP boundaries.
-   Create user stories and acceptance criteria.
-   Create wireframes and initial visual design.
-   Create system architecture and ERD.

**Deliverable:** Approved planning baseline and design package.

## Release 1 --- MVP Marketplace

-   Project setup and repository structure.
-   Authentication and business membership.
-   Manufacturer profile and review workflow.
-   Product and capability management.
-   Public manufacturer and product discovery.
-   Search, filters and pagination.
-   RFQ submission and manufacturer recipient workflow.
-   Quotation creation and buyer decision.
-   Basic admin panel and audit logging.
-   Automated tests and API documentation.

**Deliverable:** Working web marketplace demonstrating
discovery-to-quotation.

## Release 2 --- Mobile Experience

-   Mobile authentication.
-   Buyer RFQ and quotation views.
-   Manufacturer RFQ inbox.
-   Quotation response workflow.
-   Push notifications.
-   Mobile loading, error and offline states.

**Deliverable:** Companion mobile application using the shared API.

## Release 3 --- Order and Operations

-   Purchase order creation from accepted quotations.
-   Order status tracking.
-   Production updates.
-   Shipment reference and document handling.
-   Improved notification and activity history.

**Deliverable:** Extended sourcing and order lifecycle.

## Release 4 --- AI-Assisted Sourcing

-   Natural-language product and capability search.
-   Specification document extraction.
-   Quotation comparison assistance.
-   AI-generated summaries with source context and user confirmation.

**Deliverable:** Optional AI assistance that does not replace user
decisions.

## Release 5 --- Web3 Verification Experiment

-   Wallet connection in a test environment.
-   Document hash generation.
-   Smart contract for non-sensitive proof registration.
-   Proof lookup and integrity verification.
-   Security review and clear limitations.

**Deliverable:** Demonstration of a narrowly scoped blockchain
verification use case.

## Release 6 --- Production Engineering Improvements

-   Docker-based deployment.
-   CI/CD.
-   Performance and security testing.
-   Monitoring and backup validation.
-   Accessibility improvements.
-   Architecture review and documented trade-offs.

**Deliverable:** Reproducible, documented public demonstration
environment.

------------------------------------------------------------------------

# 15. Portfolio and Repository Requirements

## 15.1 Recommended Repository Structure

``` text
factorylink/
├── README.md
├── LICENSE
├── .gitignore
├── .env.example
├── docs/
│   ├── requirements/
│   │   └── SRS.md
│   ├── architecture/
│   │   ├── system-architecture.md
│   │   └── adr/
│   ├── diagrams/
│   │   ├── system-context.mmd
│   │   ├── erd.mmd
│   │   └── workflows/
│   ├── api/
│   ├── testing/
│   └── deployment/
├── apps/
│   ├── web/
│   └── mobile/
├── backend/
│   └── laravel-api/
├── services/
│   └── ai-service/
├── blockchain/
│   └── contracts/
└── infrastructure/
    ├── docker/
    └── deployment/
```

Directories for future phases may be added when implementation begins.
Do not create empty services just to make the repository look more
complex.

## 15.2 Main README Content

The repository's main README should contain:

1.  Project name and short description.
2.  Problem statement and target users.
3.  Key MVP features.
4.  Screenshots or a short demo video.
5.  Architecture diagram.
6.  Technology stack.
7.  Local setup instructions.
8.  Environment configuration instructions.
9.  Test commands.
10. Demo account instructions using non-sensitive seeded accounts.
11. Current implementation status.
12. Known limitations.
13. Roadmap.
14. License and attribution.

## 15.3 Portfolio Case Study

A portfolio case study should explain:

-   What problem the platform addresses.
-   Why the B2B manufacturing model differs from C2C e-commerce.
-   How manufacturer capabilities affect product discovery.
-   Why RFQ and quotation workflows are important.
-   How user accounts are separated from business organizations.
-   How business-level authorization is enforced.
-   How the database supports multiple manufacturers and buyers.
-   Which technical challenges were encountered and how they were
    resolved.
-   What was measured during testing.
-   What remains incomplete and what would be improved next.

The case study must distinguish implemented functionality from planned
functionality. Do not claim usage numbers, performance improvements,
security certification or production adoption unless they have been
independently measured or demonstrated.

------------------------------------------------------------------------

# 16. MVP Prioritization

The first release should focus on one complete business journey rather
than many disconnected modules.

  -----------------------------------------------------------------------
  Priority                Module                  MVP decision
  ----------------------- ----------------------- -----------------------
  P0                      Authentication          Required

  P0                      Business profile and    Required
                          membership              

  P0                      Manufacturer review     Required

  P0                      Product catalogue       Required

  P0                      Manufacturer and        Required
                          product discovery       

  P0                      RFQ workflow            Required

  P0                      Quotation workflow      Required

  P0                      Basic admin tools       Required

  P0                      Authorization and audit Required
                          trail                   

  P1                      In-app notifications    Include if feasible in
                                                  MVP

  P1                      Mobile application      Release 2

  P1                      Email notifications     After core workflow

  P2                      Purchase orders and     Later release
                          production tracking     

  P2                      AI sourcing assistant   Later release

  P2                      Blockchain verification Later release

  P3                      Payment, escrow and     Outside current
                          logistics integrations  portfolio scope
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 17. Open Questions

The following decisions should be resolved during detailed design:

1.  Will a single user be allowed to own or represent both buyer and
    manufacturer businesses?
2.  Will an RFQ be sent to one selected manufacturer or multiple
    manufacturers?
3.  Will manufacturer applications require uploaded evidence, manual
    review, or both?
4.  Which product categories and manufacturing capability attributes
    will be supported initially?
5.  Will the MVP allow direct messaging, or will all communication occur
    through RFQ and quotation records?
6.  Will product listings require administrator moderation before
    publication?
7.  Which countries, currencies and languages will be supported in the
    first demonstration?
8.  What file types and maximum sizes will be accepted?
9.  What is the retention policy for rejected applications, RFQs and
    uploaded files?
10. Which hosting provider and deployment architecture will be used for
    the public demo?

These questions should be answered before the relevant feature is
implemented. Reasonable initial defaults may be selected and recorded as
design decisions.

------------------------------------------------------------------------

# 18. Final Product Definition

FactoryLink is a portfolio-scale B2B manufacturing marketplace designed
to connect manufacturers with business buyers through structured product
discovery, manufacturing capability profiles, requests for quotation and
quotation management.

The MVP will demonstrate a complete and secure sourcing workflow:

**Manufacturer onboarding → Profile approval → Product publication →
Buyer discovery → RFQ submission → Manufacturer quotation → Buyer
decision.**

The project will be developed incrementally using a shared backend API
for web and mobile clients. AI, blockchain, order management and
advanced operational features will be introduced only after the core
marketplace is working and tested.

The primary engineering objective is not to maximize the number of
technologies used. It is to demonstrate the ability to understand a
business problem, translate it into requirements, design a maintainable
system, implement reliable workflows, test security boundaries, deploy
the application and explain the engineering decisions clearly.

------------------------------------------------------------------------

**End of Document**
