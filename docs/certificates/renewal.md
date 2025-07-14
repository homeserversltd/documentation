# Certificate Renewal Guide

## 📅 Certificate Expiration Reminder

SSL/TLS certificates expire every 2 years maximum due to browser security policies. When certificates expire, browsers will show security warnings. It's just a reminder that it's time to renew.

**What happens when certificates expire:**
- Browsers display security warnings.
- Users see "Your connection is not private" or similar messages
- Unimpeded HTTPS access is blocked until the certificate is renewed

**Simple solution:** Set a calendar reminder for 1-2 months before your certificate expires, and follow the renewal process below.

---

## Certificate Renewal 

### HomeServer Admin Interface

The easiest way to renew your certificates is through the HomeServer admin interface:

1. **Access Admin Panel**: Navigate to your HomeServer and go to the Admin tab
2. **Find Certificate Section**: Look for the "Install Certificate" button
3. **Refresh Certificate**: Click the "Refresh Certificate" button to generate a new certificate
4. **Follow the instructions at the bottom of the install instructions**
5. **You will also recieve instructions when you hit the confirm button to refresh your certificate.**

**Important Notes:**
- When you refresh the certificate, you'll be temporarily disconnected from the website
- You'll need to install the new certificate on each device that had the previous certificate
- The system will provide step-by-step instructions during the process
!!! warning "Connection Lost During Renewal"
    If you lose connection to your HomeServer during the certificate renewal process, follow these recovery steps:

    1. **Open Private Window**
       - Launch an incognito/private browser window
       - This ensures a clean session without cached certificates

    2. **Reconnect to HomeServer**
       - Navigate back to your HomeServer website
       - You may see security warnings - this is expected

    3. **Install New Certificate**
       - Download the new certificate when prompted
       - Follow the installation instructions carefully

    4. **Restart Browser**
       - Close all browser windows completely
       - Reopen your browser to ensure the new certificate is loaded

---

**Next Steps**: If you need to install or troubleshoot CA certificates on client devices, see the [CA Certificate Troubleshooting Guide](troubleshooting.md). 