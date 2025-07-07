# YV Hackathon July 7th-11th 2025

> [!NOTE]
> This repository of software is provided exclusively for participants of the “Building the YouVersion Platform Hackathon” during the above dates (the “hackathon”).
> It is provided solely for internal experimentation and prototyping during and as a part of the hackathon. No other rights are granted to use, copy, modify, distribute, or sublicense this repository of software or any derivatives thereof.
> All content remains the exclusive property of YouVersion and is protected by applicable copyright and intellectual property laws. YouVersion reserves all of its rights.

# Important Links

* [Developer Hub](https://developers.youversion.com/)
* [Platform Team Liaisons](https://docs.google.com/document/d/1UF0w_MFoGCEhZLhI1OFI7kYtJlaSqY0k_HhhgU1iX-M/edit?usp=sharing)
* [YouVersion on GitHub](https://github.com/youversion)
* [LLM SDK instructions](https://api-dev.youversion.com/llms.txt)
* [Create a staging account](https://staging.bible.com)
* [OpenAPI spec](https://gitlab.com/lifechurch/youversion/apis/platform/transformers/-/blob/main/spec/openapi.yaml?ref_type=heads)

# Important Steps to Start Hackathon Week

## 1. Register an app in the Dev Portal
* [Go to the Developer Hub](https://developers.youversion.com/)
* Click "Join the YouVersion Platform"
* Click "Sign in to YouVersion (top left box)
* Click "Manage Apps" (leftmost box)
* Click "New Application" button (top right)
* Your "App Id" is your public identifier to the API. Copy it

## 2. Try hitting the APIs
Go to the [Dev Portal examples](https://developers.youversion.com/examples) (there's also a top-nav page).
Enter your App Id and try some cURL calls.

Endpoints and usage are also listed in this [llms.txt](https://api-dev.youversion.com/llms.txt)

NOTE: If you want to implement "Sign in with YouVersion", see below. A couple of the example cURLs require a "LAT", which is addressed there.

## 3. Use the APIs in your projects
If you give an AI a cURL call, it can figure out how to implement it in your language. Try a prompt like:

```Fetch Bible text in my app using my app id 1234abc and this curl call (paste both the call and response)```

## 4. Sign in with YouVersion
Sensitive API calls require login, which produces a Limited Access Token (LAT). You can get a LAT to test with the above cURLs [from this example site](https://lifechurch.gitlab.io/youversion/apis/platform/yvp-login-flutter/) **MUST USE A YV STAGING ACCOUNT**

To implement "Sign in with YouVersion" in your project, you can use these [dev docs designed for humans and AIs](https://www.notion.so/yvproduct/Dev-Docs-Sign-In-w-YVP-Platform-Agnostic-DIY-SDK-1eaf1f2d1b9280108ffdf8c4f13e01a5?source=copy_link)

That example site is a Flutter project you can look at here: <https://gitlab.com/lifechurch/youversion/apis/platform/yvp-login-flutter>
 

# FAQ

* How do I find a list of Bibles available to use?
    > You can access the API at `https://api-dev.youversion.com/v1/bibles` for a full list of available versions.
* What state are the SDKs in?
    > The Swift SDK is in a decent state for usage. We haven't spent the same time with the Flutter SDK. There is also a Javascript SDK available for usage.
* What is a LAT?
    > It is a "Limited Access Token". It takes your YouVersion OAuth token and limits the resources it can access. It's essentially the same concept as OAuth scopes. Just a custom implementation rolled a little different. For calls that need user authentication you can add the LAT to the `X-App-Id` header to the API request and remember to use your staging username & password for testing.
* What is a "language range"?
    > In our newest API standards, we are attempting to encapsulate more industry standards in a way that will allow us to scale to every language in the world! Our architecture team has written up [some excellent documentation](https://www.notion.so/yvproduct/Locales-Language-Tags-3e9cd9017f44421e865506e8252f8126?source=copy_link) for us. But if you don't want to read and learn all that right now the TL;DR is that you can just send the old language tags you are used to sending in the `language_ranges` query parameter.
* Why are the APIs versioned weird?
    > Well, we try to follow the Google API Design Gudie as closely as possible. Over the years it has changed and we've also changed to more closely align with the documented standards. As part of Platform we decided to align stricly with the design guide's way of versioning. Why not v5 then you ask? Well, we may still end up at v5 which is a disucssion being had with staff level API engineers.
* What is USFM?
    > USFM stands for Unified Standard Format Markers. It's a plain text markup system used for encoding digital texts of scripture translations. USFM primarily focuses on identifying the content and structure of the text rather than its formatting. It's widely used in the Bible translation community, particularly within the Paratext software. It is designed to standardize how different elements within a scripture text (like chapters, verses, headings, footnotes, etc.) are marked up and identified in a digital format. We use it internally as an identifier for our Book, Chapter and Verse objects.
* I need Google Cloud resources, where should they go?
    > Any Google Cloud resources you need should be added to the "Hackathon July 2025" Project. All hackathon participants should have access to it in console.cloud.google.com logging in with your youversion.com email.
