# Noori's Barber - Booking Website

A modern and professional website for Noori's Barber, featuring an integrated booking system, admin panel, and automated email confirmations.

!Next.js
!React
!TypeScript
!Tailwind CSS

## 📋 Table of Contents

- Overview
- Features
- Tech Stack
- Project Structure
- Getting Started
- API Documentation
- Environment Variables
- Deployment

## 🎯 Overview

This is a full-stack web application for a modern barbershop, which includes:
- A responsive website with a clean, modern design and dark/light mode support.
- A fully functional online booking system.
- Automated email confirmations for customers.
- Email notifications to the salon for new bookings and contact form submissions.
- A secure admin panel to view and manage bookings.

## ✨ Features

### For Customers
- 🏠 **Homepage:** An elegant landing page showcasing the salon, a dynamic list of services, a gallery, and testimonials.
- 📅 **Online Booking:** An interactive booking form with a date picker, time slot selection, and barber selection.
- ✉️ **Email Confirmation:** Customers receive an automatic email receipt upon booking.
- 💈 **Services Page:** A detailed overview of all services, neatly organized by category.
- 📞 **Contact Page:** Displays opening hours, address, a map, and a functional contact form.

### For Administrators
- 🔐 **Admin Panel:** A password-protected page to manage all incoming bookings.
- ✅ **Status Management:** Mark bookings as "handled" or "unhandled" to keep track of the schedule.
- 📊 **Booking Overview:** View all booking details, including customer information, chosen service, and any special notes.

## 🛠 Tech Stack

### Frontend
- **Next.js** - React framework with App Router.
- **React** - UI library for building user interfaces.
- **TypeScript** - For type-safe JavaScript.
- **Tailwind CSS** - A utility-first CSS framework for rapid UI development.
- **react-day-picker** - A flexible and customizable date picker component.
- **date-fns** - For modern date/time manipulation.

### Backend & API
- **Next.js API Routes** - For creating serverless API endpoints.
- **Nodemailer** - For sending emails via an SMTP server (e.g., Gmail).

## 📁 Project Structure

```
nooris-barber/
├── app/
│   ├── page.tsx              # Homepage
│   ├── layout.tsx            # Root Layout
│   ├── globals.css           # Global Styles
│   ├── admin/
│   │   └── page.tsx          # Admin Panel
│   ├── api/
│   │   ├── admin/login/route.ts # Admin login logic
│   │   ├── bookings/route.ts # GET & PATCH for bookings
│   │   ├── contact/route.ts  # POST for contact form
│   │   └── send/route.ts     # POST for creating bookings & sending emails
│   ├── boking/
│   │   └── page.tsx          # Booking Page
│   ├── contact/
│   │   └── page.tsx          # Contact Page
│   └── services/
│       └── page.tsx          # Services Page
├── components/
│   ├── BookningForm.tsx      # Booking Form Component
│   ├── Footer.tsx            # Footer Component
│   ├── Navbar.tsx            # Navbar Component
│   └── ThemeToggle.tsx       # Dark/Light mode toggle
├── data/
│   ├── availability.ts       # Defines working hours and breaks
│   ├── bookings.json         # Local database for bookings (for development)
│   └── services.ts           # Central list of all services
├── public/
│   ├── images/               # Site images (hero, gallery)
│   └── logo.png              # Site logo
├── .env.local                # Environment variables (not committed to git)
├── package.json
└── tsconfig.json
```

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:
- **Node.js** v20.x or later
- **npm**, **yarn**, or **pnpm**

### Installation

1.  **Clone the repository**
    ```bash
    git clone <repository-url>
    cd nooris-barber-next-js
    ```

2.  **Install dependencies**
    ```bash
    npm install
    ```

3.  **Set up environment variables**

    Create a `.env.local` file in the project root and add the following variables.

    ```env
    # For sending emails via Gmail
    SMTP_USER=your-email@gmail.com
    SMTP_PASS=your-gmail-app-password

    # For logging into the /admin page
    ADMIN_PASSWORD=your-secret-admin-password
    ```

    > **Note:** For Gmail, you must use an **App Password**. Go to Google Account Settings → Security → 2-Step Verification → App passwords to generate one.

4.  **Start the development server**
    ```bash
    npm run dev
    ```

    Open http://localhost:3000 in your browser.

## 📡 API Documentation

### `POST /api/send`

Handles new bookings. It sends an email notification to the salon and a confirmation email to the customer.

### `POST /api/contact`

Handles contact form submissions. It sends the message to the salon's email and a confirmation to the sender.

### `POST /api/admin/login`

Securely handles admin login by verifying the password on the server side.

### `GET /api/bookings`

*For local development only.* Fetches all bookings from `data/bookings.json`.

### `PATCH /api/bookings`

*For local development only.* Updates a booking's `handled` status in `data/bookings.json`.

## 🔐 Environment Variables

Create a `.env.local` file with the following:

| Variable | Description | Example |
| :--- | :--- | :--- |
| `SMTP_USER` | The email address used for the SMTP server. | `info@noorisbarber.se` |
| `SMTP_PASS` | The app-specific password for the email account. | `abcd efgh ijkl mnop` |
| `ADMIN_PASSWORD`| The password to access the `/admin` page. | `supersecret` |

## 🚢 Deployment

This project is optimized for deployment on **Vercel**.

1.  **Push your code** to a GitHub, GitLab, or Bitbucket repository.
2.  **Import the project** on your Vercel Dashboard.
3.  **Configure Environment Variables:** Go to your project's **Settings → Environment Variables** on Vercel and add the `SMTP_USER`, `SMTP_PASS`, and `ADMIN_PASSWORD` variables.
4.  **Deploy!** Vercel will automatically build and deploy your site.

> **Important:** The feature to save bookings to a JSON file will **not** work on Vercel due to its read-only file system. The application is configured to handle this gracefully by relying on email notifications for booking management. The admin panel will not display bookings in a production environment. For a full-featured admin panel, a database (e.g., Vercel Postgres) is required.
