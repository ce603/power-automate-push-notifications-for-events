# 📲 Push Notification Reminder for Outlook 365 Calendar Events

## 📄 Description
This Power Automate flow sends a **push notification to your mobile device approximately 10 minutes before any calendar event** that is categorized as `Push Notification`.

---

## 🔧 Setup Instructions

### 1. Install Power Automate App
- Download **Microsoft Power Automate** from the [Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.flow) or [Apple App Store](https://apps.apple.com/app/microsoft-power-automate/id1408018998).
- Sign in using the **same Microsoft account** associated with your Outlook calendar and Power Automate portal.
- Ensure **notifications are enabled** for the app in your phone's system settings.

---

### 2. Create "Push Notification" Category in Outlook
To tag events for notifications, you’ll need a category named exactly:

> `Push Notification` *(case sensitive)*

**Steps to add it:**
1. Go to [Outlook.com](https://outlook.com) and sign in.
2. Click the **gear icon** in the top right → select **“View all Outlook settings”**.
3. Navigate to:  
   `Mail` → `Customize Actions` → `Categories`
4. Add a new category named **Push Notification** (choose any color you like).
5. The name must match exactly: `Push Notification`

---

### 3. Create Required Connections in Power Automate
1. Go to [Power Automate](https://make.powerautomate.com).
2. In the left sidebar, click **Connections**  
   *(or click "More > Connections" if it’s not directly visible)*.
3. Click **+ New connection** in the top-left.
4. Search for and create the following connections:
   - `Office 365 Outlook`
   - `Notifications` *(or `Push Notification` if that’s what your environment labels it)*

Make sure both connections are **authenticated and marked as connected**.

---

### 4. Configure the Flow
1. Import or create the flow that uses the **"When an upcoming event is starting soon (V3)"** trigger.
2. Set the `Look-Ahead Time` parameter to **10** (minutes).
3. Add a **Condition** after the trigger (within a `For each` loop) with this expression:

   contains(items('Apply_to_each')?['categories'], 'Push Notification')

4. Under the **True** path, add the **Send me a mobile notification** action with your desired message.

> ✅ Tip: You can customize the message with dynamic values like event subject, time, etc.

---

## ✅ Usage

1. Create or edit an event in your Outlook calendar.
2. Assign it the **Push Notification** category.
3. As long as the flow is turned on, you will receive a **mobile push notification** 10 minutes before that event starts.

> Events can have multiple categories — just make sure `"Push Notification"` is one of them.

---

## 💬 Notes

- This flow relies on the **default calendar** associated with your Office 365 account.
- Make sure your **calendar time zone** and **phone’s time zone** are in sync to avoid timing mismatches.
- You can adjust the `Look-Ahead Time` if you prefer a different notification window.

---

## 🧪 Troubleshooting

- **No notification?**
  - Ensure the category name is exactly `Push Notification`.
  - Verify your flow has run (check Run History).
  - Confirm that your phone has the Power Automate app installed, signed in, and with notifications enabled.
  - Ensure the calendar event starts within the `Look-Ahead Time` and was created in your default calendar.
