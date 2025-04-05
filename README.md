# Technical Specifications Document

## 1. Title Page
- **Project Name**: Airline-Booking-App
- **Version**: 1.0
- **Date**: April 05, 2025
- **Author(s)**: Bootcamp Group (Gerald Narisma, Kitz Saberon, John Michael Catapia)

## 2. Table of Contents
1. [Introduction](#3-introduction)
2. [Overall Description](#4-overall-description)
3. [Visual Mockup Reference](#5-visual-mockup-reference)
4. [Features](#6-features)
5. [Functional Requirements](#7-functional-requirements)
6. [Non-Functional Requirements](#8-non-functional-requirements)
7. [Data Requirements](#9-data-requirements)
8. [External Interface Requirements](#10-external-interface-requirements)
9. [Glossary](#11-glossary)
10. [Appendices](#12-appendices)

## 3. Introduction
- **Purpose**: The purpose of this application is to provide a seamless platform for users to search, book, and manage airline flights, while allowing airline administrators to manage their offerings.
- **Scope**: The app will include user registration/login, flight search and booking, payment processing, ticket generation, and admin flight management. It will not include real-time flight tracking or integration with airline APIs in the first version.
- **Definitions, Acronyms, and Abbreviations**: 
  - **API**: Application Programming Interface
- **References**: None

## 4. Overall Description
- **Product Perspective**: This is a standalone web-based application with separate roles for users and administrators.
- **Product Functions**: 
  - User registration and login
  - Flight search and booking
  - Ticket generation
  - Payment processing
  - Admin flight management
- **User Classes and Characteristics**: 
  - **End Users**: Books flights, views bookings, and receives tickets
  - **Admin Users**: Manages airline data and flight details
- **Operating Environment**: 
  - **Client**: Web browser (Chrome, Firefox, Edge)
  - **Server**: Node.js backend, MongoDB database
- **Assumptions and Dependencies**: 
  - Internet connection required
  - Compatible device (desktop/mobile)
  - Secure payment gateway integration

## 5. Visual Mockup Reference
- **Link or Screenshot**: ![Mockup](mockup_link.png)

## 6. Features
- **User Registration and Login**: Users (travelers and admins) can register and log in securely.
- **Flight Search and Booking**: Users can search for available flights based on locations and dates, and make bookings.
- **Passenger Management**: Users can add passenger details (name, email, baggage info, etc.) during booking.
- **Booking History**: Users can view a list of their current and past flight bookings.
- **Admin Dashboard**: Admins can manage airline details, flights, and monitor overall booking activity.
- **Payment Gateway Integration**: Users can securely make payments for their bookings via a payment gateway.
- **Ticket Generation**: The system generates digital tickets after a successful booking and payment.
- **Email Notifications**: Users receive email confirmations for successful bookings and payments.
- **Responsive Interface**: The application is designed to be mobile-friendly and accessible on all devices.
- **Role-Based Access Control**: Different access levels are provided for users and admins to ensure secure operations.


## 7. Functional Requirements
### Use Cases
- **Use Case 1**: User Registration
  - **Title**: Register a new user
  - **Description**: Users can create an account with their personal details and a password.
  - **Actors**: End User
  - **Preconditions**: User is on the registration page.
  - **Postconditions**: New user account is created and the user is logged in.
  - **Main Flow**: User fills in registration form > Clicks "Register" > System validates and creates account > Logs user in.
  - **Alternate Flows**: 
    - User inputs invalid data > System shows appropriate error message.
    - Email already exists > System displays duplicate email warning.

- **Use Case 2**: Flight Booking
  - **Title**: Book a flight
  - **Description**: Users can search and book flights based on availability.
  - **Actors**: End User
  - **Preconditions**: User must be logged in.
  - **Postconditions**: Booking is saved and confirmation is shown.
  - **Main Flow**: User searches flights > Selects flight > Enters passenger details > Proceeds to payment > Booking confirmed.
  - **Alternate Flows**: 
    - No flights available > System shows “no flights found” message.
    - Payment fails > System notifies user to retry.

### System Features
- **Feature 1**: User Registration and Login
  - **Description**: Allow users to register and authenticate into the system.
  - **Priority**: High
  - **Inputs**: Name, email, password, mobile number
  - **Processing**: Validate user data, store securely
  - **Outputs**: Confirmation and redirection to dashboard
  - **Error Handling**: Show message for invalid or duplicate input

- **Feature 2**: Flight Search and Booking
  - **Description**: Allow users to search available flights and make a booking.
  - **Priority**: High
  - **Inputs**: Departure and arrival location, dates
  - **Processing**: Query database for available flights
  - **Outputs**: List of flights; booking confirmation
  - **Error Handling**: Show message when no flights are available

- **Feature 3**: Payment Gateway Integration
  - **Description**: Securely process flight payments.
  - **Priority**: High
  - **Inputs**: Payment details (card, method)
  - **Processing**: Validate and process payment via API
  - **Outputs**: Payment confirmation or failure message
  - **Error Handling**: Handle failed transactions gracefully

- **Feature 4**: Ticket Generation
  - **Description**: Generate digital ticket after successful booking and payment.
  - **Priority**: Medium
  - **Inputs**: Booking and passenger data
  - **Processing**: Create ticket and assign seat
  - **Outputs**: Downloadable or viewable ticket
  - **Error Handling**: Notify if ticket generation fails

## 8. Non-Functional Requirements
- **Performance**: 
  - Pages should load within 3 seconds under normal network conditions.
- **Security**: 
  - Passwords must be hashed.
  - Sensitive user and payment data must be encrypted (HTTPS).
- **Usability**: 
  - Clean, mobile-friendly UI for all users.
- **Reliability**: 
  - 99.9% uptime expected; support for redundant backups.
- **Supportability**: 
  - Code should follow best practices with clear documentation and modular architecture.

## 9. Data Requirements
- **Data Models**:
  - **Airline_info**: { airlineId, name, logo, email, mobileNumber, address }
  - **User_info**: { userId, firstName, lastName, email, password, mobileNumber, dateOfBirth, role, createdOn, updatedOn }
  - **Flight_details**: { flightId, fromLocation, toLocation, departureDate, arrivalDate, seatsAvailable, price, createdOn, updatedOn }
  - **Booking_details**: { bookingId, userId, flightId, passengers, bookingDate, flightType, seatNumber, totalAmount, createdOn, updatedOn }
  - **Passenger_details**: { passengerId, userId, firstName, lastName, email, mobileNumber, baggageDetails, otherDetails }
  - **Payment_details**: { paymentId, bookingId, amount, paymentDate, paymentMethod, status, createdOn, updatedOn }
  - **Ticket_info**: { ticketId, userId, passengerId, firstName, lastName, class, fare }

- **Database Requirements**: 
  - Use MySQL or PostgreSQL for relational data integrity.
  - Establish foreign key constraints between related tables.

- **Data Storage and Retrieval**: 
  - All user data, bookings, and tickets must be securely stored and retrievable by authorized users only.

- **ERD**:
  - [View ERD Diagram](https://app.diagrams.net/#G1dhoeZgBwm6gxpbuvow-XHJuoxpuBmcgT#%7B%22pageId%22%3A%22F0WhinVh_l8tOQ3vHs6p%22%7D)


## 10. External Interface Requirements
- **User Interfaces**: 
  - Registration/Login page
  - Flight Search and Booking page
  - Passenger Details form
  - Booking Confirmation and Ticket page
  - Admin Dashboard

- **API Interfaces**: 
  - Payment Gateway API (e.g., Stripe or PayPal)
  - Email Service API for confirmations (e.g., SendGrid)

- **Hardware Interfaces**: 
  - None required; accessible via standard web browsers.

- **Software Interfaces**: 
  - Database: MySQL/PostgreSQL
  - Frontend: HTML, CSS, JS (React/Bootstrap)
  - Backend: PHP/Node.js (based on implementation choice)

## 11. Glossary
- **Booking ID**: Unique identifier for a flight booking.
- **Passenger**: An individual for whom the flight is being booked.
- **Ticket**: A digital proof of confirmed booking.
- **Flight Type**: Can be one-way or round-trip.
- **Payment Status**: Indicates whether payment was successful or failed.

## 12. Appendices
- **Supporting Information**: 
  - Sample mockups
  - User flow diagrams
  - Test cases

- **Revision History**: 
  - **v1.0**: Initial draft – April 5, 2025

