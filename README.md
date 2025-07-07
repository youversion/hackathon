# YV Hackathon July 7th-11th 2025

> [!NOTE]
> This repository of software is provided exclusively for participants of the “Building the YouVersion Platform Hackathon” during the above dates (the “hackathon”).
> It is provided solely for internal experimentation and prototyping during and as a part of the hackathon. No other rights are granted to use, copy, modify, distribute, or sublicense this repository of software or any derivatives thereof.
> All content remains the exclusive property of YouVersion and is protected by applicable copyright and intellectual property laws. YouVersion reserves all of its rights.

# Important Links

* [Developer Hub App Registration](https://developers.youversion.com/platform/apps)

# FAQ

* How do I find a list of Bibles available to use?
    > You can access the API at `https://api-dev.youversion.com/v1/bibles` for a full list of available versions.
* What state are the SDKs in?
    > The Swift SDK is in a decent state for usage. We haven't spent the same time with the Flutter SDK. There is also a Javascript SDK available for usage.
* What is a LAT?
    > It is a "Limited Access Token". It takes your YouVersion OAuth token and limits the resources it can access. It's essentially the same concept as OAuth scopes. Just a custom implementation rolled a little different. For calls that need user authentication you can add the LAT to the `X-App-Id` header to the API request.
* What is a "language range"?
    > In our newest API standards, we are attempting to encapsulate more industry standards in a way that will allow us to scale to every language in the world! Our architecture team has written up [some excellent documentation](https://www.notion.so/yvproduct/Locales-Language-Tags-3e9cd9017f44421e865506e8252f8126?source=copy_link) for us. But if you don't want to read and learn all that right now the TL;DR is that you can just send the old language tags you are used to sending in the `language_ranges` query parameter.
