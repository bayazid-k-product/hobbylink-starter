```
# HobbyLink - Complete Application Documentation

## Project Overview

**HobbyLink** is a global social networking mobile application that connects people based on shared interests, hobbies, and activities in real-world settings. The platform bridges the gap between digital connections and physical interactions by enabling users to find activity partners, create events, and build meaningful relationships with like-minded individuals in their geographic vicinity.

**Tagline:** "Same interests, real connections"

---

## Table of Contents

1. [Core Features](#core-features)
2. [User Journey & Screens](#user-journey--screens)
3. [Database Schema](#database-schema)
4. [Technical Architecture](#technical-architecture)
5. [Monetization Strategy](#monetization-strategy)
6. [Safety & Moderation](#safety--moderation)
7. [Development Roadmap](#development-roadmap)
8. [Success Metrics](#success-metrics)
9. [Design Guidelines](#design-guidelines)
10. [Glossary](#glossary)

---

## Core Features

### 1. User Registration & Authentication

#### Splash Screen
- Duration: 2 seconds
- Displays HobbyLink logo and tagline
- Red theme (primary brand color)

#### Onboarding Screen
- Brief application explanation
- Two primary buttons: **Sign In** and **Create Account**

#### Registration Screen
**Fields:**
- Display Name (required, max 30 chars)
- Username (required, unique, alphanumeric, max 20 chars)
- Password (required, min 8 chars, must include uppercase, lowercase, number, special character)
- Confirm Password (must match)
- Country Selection (dropdown with all countries)
- Profile Picture (optional, max 5MB, JPG/PNG/WEBP)

**Special Case - Minor Users (Under 18):**
- Additional field: **Guardian Email** (required)
- Must be different from user's email
- Verification email sent to guardian
- Account not activated until guardian approves

**Actions:**
- Create Account button (validates all fields)
- "Already have an account?" link (navigates to Sign In)

#### Email Verification Screen
- Single field: Email Address (required, valid format)
- **Send OTP Button** (triggers email verification)
- OTP expires after 5 minutes

#### OTP Verification Screen
- Single field: OTP Code (6-digit numeric)
- Auto-submit when 6 digits entered
- **Resend OTP Button** (60-second cooldown)
- 3 attempts allowed, then 15-minute lockout

#### Sign In Screen
**Options:**
1. Email/Username + Password login
2. Forgot Password (OTP sent to email → Reset password)
3. Google Sign-In (extracts name, email, profile photo)
4. Microsoft Sign-In (extracts name, email)

### 2. Profile Management

#### Profile Creation/Edit Screen
**Sections:**

1. **Profile Photo**
   - Circular display
   - Edit icon (camera) for updates

2. **Personal Information**
   - Display Name (editable)
   - Username (editable with uniqueness check)
   - Country (editable)
   - Bio/About Me (max 500 characters)

3. **Interests Selection**
   - Searchable list of pre-defined interests
   - Categories: Sports, Arts & Culture, Lifestyle, Adventure, Social, Learning
   - Multi-select (min 3, max 15)
   - Chips display for selected interests

4. **Social Media Links** (Optional)
   - Facebook, Instagram, Twitter/X, WhatsApp
   - Format validation

**Actions:**
- **Save Profile** (validates all fields)
- **Cancel** (discards changes)
- **Delete Account** (requires confirmation)

### 3. Home Page (Main Dashboard)

#### Top Section
- **Welcome Notification:** "Welcome back, [DisplayName]!"
- **Top Right:** App Logo (clickable to Home)
- **Top Left:** Burger Menu (side drawer navigation)

#### Middle Section
1. **"Complete Your Profile" Banner** (if profile incomplete)
   - Full-width with gradient background
   - **Complete Profile Button** → navigates to Profile Edit

2. **Activity Partner Search**
   - **Title:** "Find an activity partner"
   - **Text Box:** Multi-line input (max 1,000 chars)
   - **Search Button:** Triggers AI analysis and navigates to Search Results

3. **Secondary Action Buttons**
   - **Right Side:** "Create Event" → navigates to Event Creation
   - **Left Side:** "AI Assistant" → navigates to AI Chat

#### Bottom Navigation Bar (Fixed, 5 Tabs)
1. **Profile** (User icon)
2. **Events** (Calendar icon)
3. **Home** (House icon - default)
4. **Messages** (Envelope icon)
5. **Settings** (Gear icon)

### 4. Activity Partner Search

#### Search Results Screen
**Display:**
- List view (scrollable)
- Sorted by: Proximity (closest first), Rating (highest first), Compatibility score

**Each Result Card:**
1. Profile Photo (circular)
2. Display Name
3. Username
4. Rating (stars + number)
5. Distance (e.g., "2.3 km away")
6. Common Interests (chips, up to 3)
7. Status Indicator (Online/Recent/Offline)
8. **"Contact" Button** (Primary action)

**Contact Button Behavior:**
- Sends greeting emoji (👋)
- Cannot send another message until the other user responds
- Shows "Request sent" status
- **Cancel** option available (sends ❌ emoji, cancels request)

**Filter Options:**
- Age Range (Slider: 18-65)
- Gender (Male/Female/All)
- Activity Type
- Distance Radius (1km, 5km, 10km, 25km, 50km, Unlimited)

### 5. Chat System

#### Chat Start Process
1. User clicks **Contact** on search result
2. Emoji (👋) sent automatically
3. Recipient receives notification
4. Recipient views sender's full profile
5. Recipient decides: **Accept** (chat opens) or **Reject** (no response)

#### Chat Screen Features
- **Header:** Back arrow, Recipient's name, Online status
- **Message Area:** Text, Emojis, Images, Timestamps, Read receipts
- **Input Area:** Text field, Send button, Attachment button (optional)

#### Chat Rules
- After mutual acceptance, chat is permanently open
- No automatic expiration
- Users can exchange phone numbers and coordinate freely
- **Report User** option available

#### Voice Call Feature (Optional)
- Implemented using Agora or Vonage API
- Only voice calls (no video)
- Call button appears after mutual acceptance

#### Chat List (Messages Tab)
- Shows all active chats
- Sorted by latest message
- Shows: Contact photo, name, last message, timestamp, unread badge
- Swipe to delete/archive chat

### 6. Event System

#### Event Creation Screen
**Fields:**
1. **Event Name** (required, max 50 chars)
2. **Interests/Activity Tags** (multi-select, max 5)
3. **Event Location** (Google Maps or manual address entry)
4. **Date & Time** (cannot be in the past)
5. **Maximum Participants** (2-30, default 10)
6. **Event Description** (optional, max 2,000 chars)

#### Event Publishing
- **Publish Event Button** (event becomes visible in search)
- **Share Options:**
  - With Matched Users (select individuals to invite)
  - Via Link (generate unique link)
  - Social Media (WhatsApp, Facebook, Twitter, Instagram, Telegram)

#### Event Discovery (Events Tab)
**Categories:**
- **Popular Events:** Trending in user's area
- **My Events:** Created or joined events
- **Event Search:** Search by name, interest, location, date

#### Joining an Event
1. User finds event in search
2. Clicks **"Join Event"**
3. Request sent to Event Manager
4. Manager approves/denies
5. User added to Event Group upon approval

#### Event Group (Group Chat)
- Created automatically when event has 2+ participants
- Members: All approved participants + Manager
- Features: Group chat, Event details pinned, Member list
- Only Event Manager has admin privileges

#### Event Management (Manager Only)
**Manager Privileges:**
1. **Cancel Event**
   - Can cancel anytime before the event day
   - **Cannot** cancel on the same day
   - Cancellation triggers:
     - Notifications to all participants
     - Option for participants to apply as new manager
     - AI randomly selects new manager from applicants
     - If no applicants within 24 hours → event permanently cancelled
     - New manager sets new time and location

2. **Edit Event** (time, location, participant limit, description)
3. **Remove Participant** (with notification)
4. **Send Announcements** (mass message to all members)

### 7. AI Assistant (Chatbot)

#### AI Assistant Screen
- Dedicated chat interface
- **Purpose:** Provide activity recommendations based on user's location
- **Conversation Style:** Natural, human-like

#### Capabilities
- Answers questions about activities (e.g., "Where can I play paddle tennis near me?")
- Suggests local places for activities (e.g., "Best gyms in Cairo")
- Provides general activity advice
- Engages in casual conversation

#### Limitations
- **Does NOT save conversations** (100% ephemeral)
- Each session starts fresh
- Does not remember user preferences
- Cannot make matches between users

### 8. Ratings System

#### Rating Trigger
- After a meetup/activity or event
- App prompts both users to rate each other
- Notification: "Rate your experience with [Username]"

#### Rating Interface
1. **Star Rating (1-5)** (required)
   - 1 = Poor, 5 = Excellent
2. **Comment** (optional, max 300 chars)
3. **Rating Tags** (optional, pre-set tags like Punctual, Fun, Friendly)

#### Rating Calculation
- Each user has: Average Rating (out of 5)
- Total number of ratings
- Updated in real-time with each new rating
- Low ratings are averaged with all others

### 9. Settings Screen

#### Settings Categories
1. **Language Settings:** All world languages (100+), default English, persists after restart
2. **Country Settings:** Update country
3. **Account Settings:**
   - Change Password (current password + new password + confirmation)
   - Change Email (new email + OTP verification)
   - Delete Account (requires confirmation)
4. **Privacy & Security:** Blocked users, Reported content, 2FA
5. **Notifications Settings:** Toggle each notification type
6. **Appearance:** Dark Mode toggle, Theme color, Font size
7. **Help & Support:** FAQ, Contact Support, Report a Problem
8. **About:** App version, Privacy Policy, Terms of Service

### 10. VIP Subscription System

#### Subscription Tiers
**Free Tier (Basic):**
- Send only emoji (👋) to contact others
- See ads (banner/native ads)
- Normal search ranking
- Limited to 5 active contacts per week
- Basic support

**VIP Tier (Premium):**
- Send text messages (custom messages)
- No ads (entirely ad-free)
- Exclusive VIP badge (👑) next to name
- Priority in search results
- Unlimited contacts
- Premium support
- Highlighted profile
- Can see who viewed their profile

#### Subscription Plans
- **Monthly:** $9.99/month
- **Quarterly:** $24.99 (Save 17%)
- **Annual:** $79.99 (Save 33%) - available later
- **No lifetime subscription**

#### Free Trial
- **Initial:** 14 days free trial
- **Subsequent:** 7 days free trial
- For new users only
- Auto-renews unless cancelled

#### Payment Methods
- Google Play In-App Purchase (Android)
- Apple App Store In-App Purchase (iOS)

### 11. Advertising System

#### Ad Placement Strategy
**Goal:** Generate revenue without annoying users

1. **Banner Ads**
   - Location: Bottom of Home Screen (above bottom nav)
   - Location: Bottom of Search Results
   - Frequency: Limited to 3 per session

2. **Native Ads**
   - Blends with app content
   - Appears in: Search results (every 5th result)
   - Appears in: Event listings
   - Looks natural and non-intrusive

3. **Sponsored Events**
   - Paid promotions by venues/businesses
   - Featured at top of Events tab
   - Clearly labeled "Sponsored"

**Ad-Free Experience:** VIP subscribers see no ads at all.

### 12. Safety & Moderation System

#### Content Moderation
- Automated profanity filter in all chat messages
- Image scanning for inappropriate content
- Report system for users to flag content/behavior

#### Reporting Flow
1. User clicks **Report** on profile or message
2. Select reason from dropdown:
   - Harassment/Bullying
   - Inappropriate content
   - Fake account
   - Underage user (misrepresented)
   - Suspicious behavior
   - Other (with description)
3. Submit report
4. Admin/moderator reviews within 24-48 hours

#### Penalty System
- **First Offense:** Warning (Notification)
- **Second Offense:** Temporary ban (7 days)
- **Third Offense:** Permanent account suspension

#### Safety Guidelines (Displayed)
- "Meet in public, crowded places"
- "Avoid meeting at night or in isolated areas"
- "Inform a friend or family member of your location"
- "Trust your instincts - if something feels wrong, leave"
- "In case of emergency, call your local police"
- "HobbyLink is not responsible for any incidents outside the platform"

---

## User Journey & Screens

### Complete User Flow

```

svgsvg

Open App → Splash Screen (2s) → Onboarding Screen
│
├── Create Account → Sign Up Screen
│ ├── Fill: Display Name, Username, Password, Confirm Password, Country
│ ├── Upload: Profile Picture (optional)
│ ├── Minor: Guardian Email
│ └── Submit → Email Verification Screen
│ └── Enter Email → OTP Screen
│ └── Enter OTP → Complete Profile Screen
│ └── Bio + Interests + Social Media
│ └── Save → Home Page
│
└── Sign In → Login Screen
├── Email/Username + Password → Home Page
├── Forgot Password → Email OTP → Reset Password → Login
├── Google Sign-In → Complete Missing Fields → Home Page
└── Microsoft Sign-In → Complete Missing Fields → Home Page

text

```
### Activity Partner Search Flow

```

svgsvg

Home Page → "Find Activity Partner" Text Box
│
├── User writes: "Need 2 people for paddle tennis at 8 PM, Nasr City"
│
├── Click "Search" → AI analyzes text
│ ├── Extracts: Activity (Paddle Tennis), Time (8 PM), Location (Nasr City)
│ └── Determines: Gender (All), Age (18-35 default)
│
├── Search Results Screen
│ ├── List of users sorted by: Distance, Rating
│ ├── Each user: Photo, Name, Rating, Distance, Common Interests
│ └── Filter options: Age, Gender, Radius
│
└── User clicks "Contact" on a profile
├── Sends 👋 emoji
├── Recipient receives notification
├── Recipient views profile → Accept/Reject
├── If Accept → Chat opens
└── If Reject → Request ends

text

```
### Event Creation & Management Flow

```

svgsvg

Home Page → "Create Event" Button
│
├── Event Form
│ ├── Name, Interests, Location (Map/Address), Date/Time, Max Participants, Description
│ └── Publish → Event Created
│
├── Share Event
│ ├── With Matched Users (select individuals)
│ ├── Via Link (generate unique link)
│ └── Social Media (WhatsApp, Facebook, etc.)
│
├── Users discover event via Search/Feed
│ ├── Click "Join Event" → Request to Manager
│ └── Manager approves/denies
│
├── After Approval → Added to Event Group
│ ├── Group chat with all participants
│ └── Manager has admin privileges
│
└── Manager Actions
├── Cancel Event (before event day)
│ ├── Notify all participants
│ ├── Participants can apply to be new manager
│ └── If no applications in 24 hours → event cancelled
├── Edit Event (time/location)
└── Remove Participant

text

```
### Ratings Flow

```

svgsvg

Activity/Event Completed → Notification: "Rate your experience"
│
├── Rating Screen
│ ├── Star rating (1-5)
│ ├── Comment (optional)
│ └── Tags (optional)
│
├── Submit Rating
│ ├── Average rating updated
│ └── Total ratings count updated
│
└── Rating displayed on profile and search results

text

```
---

## Database Schema

### users Collection
```json
{
  "uid": "string (Firebase Auth UID)",
  "displayName": "string",
  "username": "string (unique)",
  "email": "string",
  "phoneNumber": "string (optional)",
  "country": "string",
  "profileImage": "string (URL)",
  "bio": "string (max 500 chars)",
  "interests": ["array of interest IDs"],
  "socialMedia": {
    "facebook": "string",
    "instagram": "string",
    "twitter": "string",
    "whatsapp": "string"
  },
  "location": {
    "latitude": "number",
    "longitude": "number"
  },
  "city": "string",
  "isVIP": "boolean",
  "subscriptionEnd": "timestamp",
  "rating": "number (average)",
  "totalRatings": "number",
  "isMinor": "boolean",
  "guardianEmail": "string (optional)",
  "isVerified": "boolean",
  "isBanned": "boolean",
  "createdAt": "timestamp",
  "lastActive": "timestamp",
  "onlineStatus": "boolean"
}
```

svgsvg

### interests Collection

json

```
{
  "interestId": "string",
  "name": "string",
  "category": "string (Sports, Arts, etc.)",
  "icon": "string (emoji or URL)"
}
```

svgsvg

### activitySearch Collection

json

```
{
  "requestId": "string",
  "userId": "string (FK)",
  "text": "string (original search text)",
  "parsedData": {
    "activity": "string",
    "location": "string",
    "time": "string",
    "preferences": {
      "gender": "string",
      "ageMin": "number",
      "ageMax": "number"
    },
    "keywords": ["array of strings"]
  },
  "location": {
    "latitude": "number",
    "longitude": "number"
  },
  "status": "string (open/matched/expired)",
  "matchedUserId": "string (optional)",
  "createdAt": "timestamp",
  "expiresAt": "timestamp"
}
```

svgsvg

### searchResults Collection

json

```
{
  "resultId": "string",
  "requestId": "string (FK)",
  "userId": "string (FK - matched user)",
  "score": "number (compatibility score)",
  "distance": "number (in meters)",
  "viewed": "boolean",
  "contacted": "boolean",
  "createdAt": "timestamp"
}
```

svgsvg

### chatRequests Collection

json

```
{
  "requestId": "string",
  "fromUserId": "string (FK)",
  "toUserId": "string (FK)",
  "status": "string (pending/accepted/rejected/cancelled)",
  "message": "string (👋 default)",
  "createdAt": "timestamp",
  "respondedAt": "timestamp (optional)"
}
```

svgsvg

### chats Collection

json

```
{
  "chatId": "string",
  "participants": ["uid1", "uid2"],
  "lastMessage": "string",
  "lastMessageTime": "timestamp",
  "unreadCount": {
    "uid1": "number",
    "uid2": "number"
  },
  "createdAt": "timestamp",
  "isActive": "boolean"
}
```

svgsvg

### messages Collection

json

```
{
  "messageId": "string",
  "chatId": "string (FK)",
  "senderId": "string (FK)",
  "text": "string",
  "type": "string (text/image/voice)",
  "mediaUrl": "string (optional)",
  "timestamp": "timestamp",
  "readBy": ["array of UIDs"]
}
```

svgsvg

### events Collection

json

```
{
  "eventId": "string",
  "managerId": "string (FK)",
  "name": "string",
  "interests": ["array of interest IDs"],
  "description": "string (optional)",
  "location": {
    "address": "string",
    "latitude": "number",
    "longitude": "number"
  },
  "dateTime": "timestamp",
  "maxParticipants": "number",
  "currentParticipants": ["array of UIDs"],
  "status": "string (active/cancelled/completed)",
  "shareLink": "string (unique)",
  "cancelledAt": "timestamp (optional)",
  "cancellationReason": "string (optional)",
  "createdAt": "timestamp",
  "cancellationEligible": "boolean (true if not event day)"
}
```

svgsvg

### eventGroups Collection

json

```
{
  "eventId": "string (FK)",
  "messages": [
    {
      "senderId": "string",
      "text": "string",
      "timestamp": "timestamp",
      "isAnnouncement": "boolean"
    }
  ],
  "members": ["array of UIDs"],
  "pendingMembers": ["array of UIDs"],
  "createdAt": "timestamp"
}
```

svgsvg

### eventJoinRequests Collection

json

```
{
  "requestId": "string",
  "eventId": "string (FK)",
  "userId": "string (FK)",
  "status": "string (pending/accepted/rejected)",
  "createdAt": "timestamp",
  "respondedAt": "timestamp (optional)"
}
```

svgsvg

### eventCancellationQueue Collection

json

```
{
  "eventId": "string (FK)",
  "cancelledAt": "timestamp",
  "applicants": ["array of UIDs"],
  "status": "string (pending/assigned/expired)",
  "newManagerId": "string (optional - after random selection)",
  "expiresAt": "timestamp (24 hours later)"
}
```

svgsvg

### ratings Collection

json

```
{
  "ratingId": "string",
  "fromUserId": "string (FK)",
  "toUserId": "string (FK)",
  "requestId": "string (optional - FK to search)",
  "eventId": "string (optional - FK to event)",
  "rating": "number (1-5)",
  "comment": "string (optional)",
  "tags": ["array of strings"],
  "createdAt": "timestamp"
}
```

svgsvg

### reports Collection

json

```
{
  "reportId": "string",
  "reporterId": "string (FK)",
  "reportedId": "string (FK)",
  "type": "string (user/message/event)",
  "reason": "string",
  "description": "string",
  "status": "string (pending/resolved/dismissed)",
  "createdAt": "timestamp",
  "resolvedAt": "timestamp (optional)",
  "resolvedBy": "string (admin ID)"
}
```

svgsvg

### bans Collection

json

```
{
  "banId": "string",
  "userId": "string (FK)",
  "reason": "string",
  "type": "string (warning/temporary/permanent)",
  "duration": "number (days - optional)",
  "expiresAt": "timestamp (optional - if temporary)",
  "createdAt": "timestamp",
  "adminId": "string (FK)"
}
```

svgsvg

### subscriptions Collection

json

```
{
  "subscriptionId": "string",
  "userId": "string (FK)",
  "plan": "string (monthly/quarterly/annual)",
  "startDate": "timestamp",
  "endDate": "timestamp",
  "status": "string (active/expired/cancelled)",
  "paymentMethod": "string",
  "transactionId": "string",
  "autoRenew": "boolean",
  "cancelledAt": "timestamp (optional)"
}
```

svgsvg

### notifications Collection

json

```
{
  "notificationId": "string",
  "userId": "string (FK)",
  "title": "string",
  "body": "string",
  "type": "string (chat/request/event/rating/system)",
  "data": {
    "chatId": "string (optional)",
    "eventId": "string (optional)",
    "requestId": "string (optional)"
  },
  "read": "boolean",
  "createdAt": "timestamp"
}
```

svgsvg

### userDevices Collection (For FCM)

json

```
{
  "deviceId": "string",
  "userId": "string (FK)",
  "fcmToken": "string",
  "platform": "string (android/ios)",
  "deviceModel": "string",
  "appVersion": "string",
  "createdAt": "timestamp",
  "updatedAt": "timestamp"
}
```

svgsvg

---

## Technical Architecture

### Technology Stack

#### Frontend

- **Framework:** Flutter (cross-platform)
- **Language:** Dart
- **State Management:** Provider or Riverpod
- **Navigation:** GetX or GoRouter

#### Backend

- **Database:** Firebase Firestore (NoSQL, real-time)
- **Authentication:** Firebase Auth
- **Storage:** Firebase Storage (images, files)
- **Push Notifications:** Firebase Cloud Messaging (FCM)
- **Hosting:** Firebase Hosting (for web dashboard)

#### APIs & Services

- **Google Maps API:** Location selection, map integration
- **Geolocator:** User location detection
- **GeoFire:** Location-based queries (nearby search)
- **Google Gemini API:** AI text analysis for search
- **Google Gemini API:** AI Assistant (chatbot)
- **Agora/Vonage API:** Voice calling (optional)
- **AdMob:** In-app advertising

#### Third-Party Integrations

- **Google Sign-In**
- **Microsoft Sign-In**
- **Social Media Sharing SDKs**
- **Firebase Crashlytics:** Error reporting
- **Firebase Analytics:** User analytics

### Platform Support

- **Android:** 5.0 (API 21) and above
- **iOS:** 12.0 and above
- **Responsive:** Supports all screen sizes

### Performance Requirements

- Launch time: <3 seconds
- App size: <50MB (without assets)
- Battery efficient (minimal background usage)
- 60fps smooth scrolling

### Offline Behavior

- App requires internet to function
- Offline screen shows pop-up: "No internet connection"
- No offline caching (except images)

---

## Monetization Strategy

### Revenue Streams

1. **VIP Subscriptions (Primary Revenue)**
   - Monthly: $9.99
   - Quarterly: $24.99 (Save 17%)
   - 14-day free trial → 7 days later
2. **In-App Advertising**
   - Banner ads (non-VIP users)
   - Native ads (non-VIP users)
   - Sponsored content/events
3. **Business Partnerships (Future)**
   - Venue partnerships (gyms, clubs, cafes)
   - Commission on bookings
   - Featured listings

### Pricing Strategy Comparison

| **FeatureFreeVIP** |               |                  |
| ------------------ | ------------- | ---------------- |
| Contact Users      | 👋 Emoji only | Any message      |
| Ads                | ✅ Yes         | ❌ No ads         |
| Badge              | ❌ No          | ✅ 👑 VIP         |
| Search Ranking     | Normal        | Priority         |
| Active Contacts    | 5/week        | Unlimited        |
| Support            | Basic         | Premium          |
| Profile Highlight  | ❌ No          | ✅ Yes            |
| Viewed By          | ❌ No          | ✅ See who viewed |

---

## Safety & Moderation

### Content Moderation

- Automated profanity filter in all chat messages
- Image scanning for inappropriate content
- Report system for users to flag content/behavior

### Reporting Flow

1. User clicks **Report** on profile or message
2. Select reason from dropdown
3. Submit report
4. Admin/moderator reviews within 24-48 hours

### Penalty System

- **First Offense:** Warning (Notification)
- **Second Offense:** Temporary ban (7 days)
- **Third Offense:** Permanent account suspension

### Safety Guidelines (Displayed)

- "Meet in public, crowded places"
- "Avoid meeting at night or in isolated areas"
- "Inform a friend or family member of your location"
- "Trust your instincts - if something feels wrong, leave"
- "In case of emergency, call your local police"
- "HobbyLink is not responsible for any incidents outside the platform"

---

## Development Roadmap

### MVP Timeline (8 Weeks)

| **WeekMilestone** |                                                        |
| ----------------- | ------------------------------------------------------ |
| **Week 1**        | Project setup, Firebase configuration, Database design |
| **Week 2**        | Registration, Login, Profile completion                |
| **Week 3**        | Home Page, Search functionality, AI integration        |
| **Week 4**        | Search Results, Contact Request, Basic Chat            |
| **Week 5**        | Full Chat system, Notifications                        |
| **Week 6**        | Event creation, Event discovery, Event Groups          |
| **Week 7**        | Ratings, Profile View, Settings                        |
| **Week 8**        | VIP subscription, Ads integration, Testing & Polish    |

### Post-Launch Enhancements (Month 9-12)

- Voice call integration
- Event booking system (B2B)
- In-app payments (Stripe)
- Analytics dashboard

---

## Success Metrics

### User Metrics

- **Daily Active Users (DAU):** 15% of total users
- **Monthly Active Users (MAU):** 40% of total users
- **User Retention (Day 30):** 25%
- **Time Spent (Daily):** 15-20 minutes

### Engagement Metrics

- **Search Actions per User:** 5x/week
- **Event Creation Rate:** 3x/month
- **Chat Open Rate:** 70%
- **Rating Submission Rate:** 60%

### Business Metrics

- **Conversion Rate (Free → VIP):** 8-12%
- **Monthly Recurring Revenue (MRR):** $5,000+ (Year 1)
- **Customer Lifetime Value (LTV):** $75
- **Customer Acquisition Cost (CAC):** $5

### Safety Metrics

- **Reported Users:** <2% of all users
- **Ban Rate:** <0.5%
- **Positive Feedback:** >85%

---

## Future Roadmap

### Version 2.0 (Month 6-9)

- Voice calling integration
- In-app payments for bookings
- Business accounts (venues, organizations)
- Live streaming of events
- Premium analytics for users

### Version 3.0 (Year 2)

- AI-powered event recommendations
- AR-based location finding
- Group video calls
- Cryptocurrency payments
- NFT rewards system

### Version 4.0 (Year 3)

- Wearable integration (smartwatch)
- Integration with fitness apps (Strava, Fitbit)
- Machine learning for better matching
- Community forums
- Multi-language support (100+ languages)

---

## Design Guidelines

### Brand Identity

- **Name:** HobbyLink
- **Tagline:** "Same interests, real connections"

#### Color Palette

- **Primary:** Red (#E53935 or #D32F2F) - Energy, passion, urgency
- **Secondary:** White (#FFFFFF) - Clean, modern
- **Accent:** Dark Gray (#2D2D2D) - Text, contrast
- **Success:** Green (#4CAF50) - Accept, positive actions
- **Warning:** Orange (#FF9800) - Alerts, warnings
- **Background:** Light Gray (#F5F5F5) - Clean UI

#### Typography

- **Primary Font:** Roboto (Modern, clean, readable)
- **Headings:** Bold 24-32px
- **Subheadings:** Medium 16-20px
- **Body:** Regular 14-16px
- **Small text:** Light 12px

#### Design Style

- **Material Design** (Google's design system)
- **Flat Design** with subtle shadows
- **Rounded corners** (8-12px radius)
- **Consistent spacing** (8px grid system)
- **Minimalist icons** (Material Icons)
- **High contrast** for accessibility

---

## Glossary

- **OTP:** One-Time Password
- **FCM:** Firebase Cloud Messaging
- **MVP:** Minimum Viable Product
- **UI/UX:** User Interface / User Experience
- **B2B:** Business-to-Business
- **AI:** Artificial Intelligence
- **API:** Application Programming Interface
- **Firestore:** Firebase's NoSQL database
- **Gemini:** Google's AI model
- **Agora:** Voice/Video calling API

---

**End of Documentation**

This document contains the complete specification for the HobbyLink application, including all features, user flows, database schemas, technical architecture, and business strategy.

📌 **Next Steps:**

1. Review this document
2. Generate UI designs using Google Stitch
3. Generate code using Google AI Studio
4. Begin development iteration