> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Troubleshooting & FAQs

> Troubleshoot common error scenarios and find answers to frequently asked questions about Cordova Integration.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

> [accordion] What should I do if I see the following error?
>
> ```javascript Error theme={null}
> dyld: Library not loaded: @rpath/libswiftCoreGraphics.dylib
>   Referenced from: /private/var/mobile/Containers/Bundle/Application/696F0EAD-E2A6-4C83-876F-07E3D015D167/<Your_App>.app/Frameworks/<Framework_Name>.framework/<Framework_Name>
>   Reason: image not found
> ```
>
> To fix the above error message:
>
> * Set the `Embedded Content Contains Swift Code (EMBEDDED_CONTENT_CONTAINS_SWIFT)` build setting to `YES` in your app. To know more, refer to [this Apple document](https://developer.apple.com/library/archive/qa/qa1881/_index.html).
> * Ensure that you have the framework added in `Frameworks, Libraries, and Embed Content` under `Target settings` - `General`. Ensure the `Embed status` is set to 'Embed & Sign'.

> [accordion] Is Capacitor supported in Razorpay Curlec Cordova Plugin?
>
> No, we do not support Capacitor in our plugin as it has its own [dependencies](https://capacitorjs.com/docs/getting-started).

> [accordion] What is order id and how to generate it?
>
> Order creation is the primary step of the Razorpay Curlec payment flow. When a customer clicks the pay button on your app, an Order is created and a corresponding order\_id is generated in the response. This order\_id must be passed to the Razorpay Curlec Checkout options added in your Capacitor app.
> Know more about [Orders](https://razorpay.com/docs/my/api/orders/create.md).

> [accordion] What is the process for raising a request for a new feature?
>
> To raise a request for a new feature, navigate to **New Issue** → **Feature Request** on our [GitHub repository](https://github.com/razorpay/razorpay-cordova/issues/new/choose).

> [accordion] How can I update the existing **'razorpay-pod'**?
>
> * Go to your project's iOS folder and run **'pod update'** to update all the pods.\\
>
> * If you do not want to update all pods, run **'pod update razorpay-pod'**.

> [accordion] In the new M1 MacBook, why am I not able to compile the Cordova Razorpay plugin for release mode?
>
> This is because of the new changes introduced in Xcode 12.
>
> To resolve this:
>
> 1. Use [Rosetta 2](https://support.apple.com/en-us/HT211861) for launching the app on your Mac.
>
> 2. Add the following lines to Podfile:
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > Add the following code inside `post_install do |installer|`.
>
> ```javascript podfile theme={null}
> installer.pods_project.build_configurations.each do |config|
>   config.build_settings["EXCLUDED_ARCHS[sdk=iphonesimulator*]"] = "arm64"
> end
> ```
>
> Know more about [compilation errors](https://khushwanttanwar.medium.com/xcode-12-compilation-errors-while-running-with-ios-14-simulators-5731c91326e9).

> [accordion] How can I check the Razorpay Curlec Cordova Standard SDK version?
>
> To check the SDK version:
>
> 1. Open your Cordova project in your preferred code editor.
> 2. Navigate to the `config.xml` file in the root directory of your project.
> 3. Look for the `<plugin>` tag that includes the Razorpay SDK plugin. The version number is represented by `x.y.z`.

> [accordion] How can I check the Razorpay Curlec Ionic Standard SDK version?
>
> To check the SDK version:
>
> 1. Open your Ionic project in your preferred code editor.
> 2. Open the `package.json` file in the root directory of your project.
> 3. In the `dependencies` section, look for the Razorpay Curlec entry. The version number is specified next to the package name in the format `x.y.z`.

> [accordion] How can I update the Razorpay Curlec Cordova and Ionic Standard SDK version?
>
> To update the SDK version using npm, follow these steps:
>
> 1. Open the terminal or command prompt and navigate to your project directory where the `package.json` file resides.
> 2. Use the npm update command followed by the package name to update a specific package to its latest version. For example, npm update `<razorpay_package_name>` (replace `<razorpay_package_name>` with the name of the package you want to update).
> 3. If you are using a Cordova iOS application, run `cd platforms && cd ios && pod repo update && pod update` to ensure the internal iOS dependencies are updated to the versions set by the Razorpay Curlec package. This is because cocoapods may not automatically update the internal trunk spec to fetch the latest versions.
> 4. After running the update command, review the updates fetched by npm to ensure they do not introduce any breaking changes.
> 5. Conduct thorough testing to ensure that the updated packages do not adversely affect the application functionality and commit the changes.
