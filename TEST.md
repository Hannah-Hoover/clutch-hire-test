# Clutch 2025 Hiring Test

## Overview

This repository contains my code for the clutch 2025 hiring test with images.

## Project Setup

Install dependencies:

```bash
npm install
```

Launch the development server with hot-reloading:

```bash
npm run serve
```

### Landing Page
When the website is run, the first thing that is seen is the landing page below, which has a form for the user to fll out:


### Form Filled Out
The user can input their informartion into the contact form:

### Error Handling
If the user tries to submit without filling out all of the fields, they are informed that they must fill out the fields:

### Thank you Page
Once they submit with the forms filled out, a thank you page is present for 5 seconds:


### Return to form
After 5 seconds, they are returned to an empty form:


## Application Flow

1. **Display the Form:** The app shows a form for the user to fill out.
2. **Submit Data:** On submission, the form data is sent to the API endpoint using the provided API key.
3. **Thank You Message:** A thank you message is displayed for 5 seconds after submission.
4. **Repeat Process:** The form resets for the next user submission.

