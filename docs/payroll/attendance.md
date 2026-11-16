> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Attendance Setup

> Configure the attendance process in RazorpayX Payroll and integrate biometric devices as per your leave set up.

Available in
🇮🇳 India

To configure the attendance for your employees you can:

* [Track Attendance](#track-attendance).
* [Integrate, configure and track attendance](#integrate-and-configure-biometric-device) using a biometric device.

## Track Attendance

You have three options via Payroll to track the attendance of your employees.

> [accordion] Dashboard Attendance
>
> As a part of the default Payroll subscription, you can use the attendance module as applicable to your organisation. You can also enable or disable it from **Settings** on your Dashboard.

> [accordion] Custom Biometric Device
>
> You can set up a biometric device and integrate it with Payroll to track attendance. The device can use fingerprints or swipe cards to automatically log the check-in/check-out timings of all the employees and contractors in your organisation.
>
> It automatically synchronises all data with Payroll so you can see your attendance data through the web interface as well. You can set up using the [Device Configuration Flow](#integrate-and-configure-biometric-device).

> [accordion] APIs
>
> If you have your internal mechanism for maintaining leave and attendance, but would like to synchronise that data with Payroll, then you can use our API. This automates data synchronisation. For more details on APIs, check under **Settings** → **API**.

> [accordion] Jibble Integration
>
> Jibble can be connected to your Payroll account using API credentials. Unpaid employee leaves or loss of pay data can easily be fetched from Jibble and added as respective deductions. Know more about [Jibble Integration](https://razorpay.com/docs/payroll/integrations/jibble.md) for attendance.

## Integrate and Configure Biometric Device

You can integrate a CAMS device or a third-party device with Payroll to sort time management, leaves and holidays for your employees. Explore the following about the custom device integration for attendance:

* Points to note about the [biometric integration](#biometric-integration).
* Set up and configure two types of devices:
  * [Third-party device](#third-party-device-integration).
  * [CAMS device](#cams-device-integration). \


Check the [troubleshooting guide](#cams-biometric-device-troubleshooting-guide) when setting up your CAMS biometric device.

### Biometric Integration

> [!NOTE]
>
> **Handy Tips**
>
> 1. Payroll supports [these biometric devices](https://camsunit.com/product/home.html).
>
> 2. In particular, we recommend the F31 Facebot or RSP10i9. We are not compatible with the i32 Macronium.
>
> In case you already have a third-party biometric device, you can test and configure it as mentioned in the [Third-Party device integration flow](#third-party-device-integration) below.

As an Payroll user, you can directly purchase a device from the link given above. While adding the device to the cart, ensure you have added the **Biometric Integration with Razorpay Payroll System** option as well. This is necessary to set up the biometric device.

After you receive the device, you just need to power it and connect it to the internet via WiFI/LAN. All your employees, contractors and new additions get automatically pushed to the device over this connection.

Users must be associated with their fingerprints (or faces, depending on the device), and once this is done, the device automatically runs a trial for the check-in/check-out timings.

> [!NOTE]
>
> **Handy Tips**
>
> In case you have more than one account on Payroll, you can integrate the same biometric device with multiple accounts.

### Third-Party Device Integration

You can integrate a third-party biometric device with Payroll. Follow the below mentioned steps to do so:

1. To start the integration, you must first test the device's compatibility with Payroll on this site: [developer.camsunit.com](https://developer.camsunit.com/).
2. On this page, enter all the requested information. If the device is compatible, a success message appears that says **Device Verified**.
3. Purchase the [Biometric APIs](https://camsunit.com/product/cams-protocol-update-for-enabling-api-to-biometric-attendance-system.html).
4. On the checkout page, under **Add Services**, select **Razorpay - Biometric Integration with Razorpay Payroll System**, as shown.

   ![Add services drop-down menu showing integration option with RazorpayX Payroll](https://razorpay.com/docs/build/browser/assets/images/x-xpayroll-time-management-add-services.jpg)
5. You have now successfully integrated the third-party biometric device with Payroll. Refer to the rest of the [CAMS device integration flow](#cams-device-integration) to set up your new device.

### CAMS Device Integration

After you have purchased a CAMS device, you can now integrate it with Payroll. To do so, follow the steps mentioned below:

1. Visit the [CAMS unit page](http://www.camsunit.com/), and log in.

   ![CAMS log in Dashboard](https://razorpay.com/docs/build/browser/assets/images/x-xpayroll-biometric-integration1.jpg)
2. Navigate to **Device Status** and confirm if your device is online. If it does not appear online, ensure your device is connected to the internet.

   ![CAMS - Dashboard](https://razorpay.com/docs/build/browser/assets/images/x-xpayroll-biometric-integration2.jpg)
3. Click **Device Management**. Copy-paste the **Service Tag ID** into a text file.
4. In the **Device Management** tab, to the left of **Device Status** tab:
   * Click the **Manage** icon.
   * Ensure the callback URL has this value: `https://api.opfin.com/api/camsunitv3`.
   * Make sure the encryption key is empty and click on the button to generate an auth token.
   * Copy-paste the auth token into a text file as well.
5. Then go to the Payroll integrations page for CAMS. Here, enter the callback URL under **add a new device**. Also enter the **Service Tag ID** and auth token from steps 3 and 4 above.
6. Once the device setup is complete, we automatically push all of your Payroll data of employees and contractors to the device.

> [!WARNING]
>
> **Watch Out!**
>
> This process can take up to an hour. Please do not add the employee details manually to the device, since they need to be added by our system for the device to work properly.

7. Once the employees details appear on the device, you can register their fingerprints/faces on the device. The device starts syncing the data with Payroll attendance instantly.

In case your there are troubles and errors in the setup process, you can refer to the [troubleshooting guide](#cams-biometric-device-troubleshooting-guide) provided below.

### CAMS Biometric Device Troubleshooting Guide

If your CAMS biometric device has issues like synchronising check-in data with Payroll, or not displaying  all of your employees/contractors, follow the steps mentioned below.

> [accordion] No Connectivity
>
> Most of the time, the device has lost internet connectivity and that must be restored.
>
> * To check this, log in to the CAMS portal and check the **Device Status** tab as mentioned in the [CAMS device integration flow](#cams-device-integration).
> * On this page, check the device status (shown by a green dot), and the **Last device connection time**.
>
> If the device appears offline or the last connected time is not in the past couple of minutes, please check the device's internet connectivity.

> [accordion] Provide Auth Token
>
> If the device is online and is not operating, follow these steps:
>
> 1. Go to the **Device Management** tab.
> 2. Click the **Manage** icon, and check the auth token. The auth token should be the same as what you see under **Integration** → **CAMS** → **Manage** on Payroll.
> 3. Check your **callback URL**. It should have this value - `https://api.opfin.com/api/camsunitv3`.

> [accordion] Sync Employee Data
>
> If all of the above methods have failed, you can try to re-sync the employee data with the biometric device.
>
> 1. On the CAMS integration page, click on the `re-sync` button. This process can take up to 1 hour.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > **Do NOT** add your employees details to the device manually. They have to be pushed by Payroll.
>
> 1. If your employees details have been pushed to the device, register their biometrics on the device and do a trial check. The attendance data must be updated within 1 minute on Payroll.

If none of the above works, please [contact us](mailto:xpayroll@razorpay.com).

### Related Information

* [Admin Role](https://razorpay.com/docs/payroll/administrator)
* [Leaves](https://razorpay.com/docs/payroll/leaves.md)
* [Salary](https://razorpay.com/docs/payroll/salary)
