---
Creation_date: 2024-07-08 23:43
Modification_date: Monday 8th July 2024 23:43:32
Indexes:
  - "[[selenium]]"
---

----

## Selenium 2.0
- **Release Date**: July 2011
- **Key Features**:
    - **WebDriver API**: Selenium 2.0 introduced the WebDriver API, which provided a more robust and efficient way to interact with web browsers compared to the older Selenium RC (Remote Control).
    - **Support for Multiple Browsers**: WebDriver supported multiple browsers including Chrome, Firefox, Internet Explorer, and others.
    - **Improved Performance**: WebDriver's direct browser interactions made it faster and more reliable than Selenium RC, which relied on JavaScript for automation.
    - **Native Browser Interactions**: Provided the ability to interact with browser elements in a more native way, improving compatibility with modern web applications.

## Selenium 3.0
- **Release Date**: October 2016
- **Key Features**:
    - **Deprecated Selenium RC**: Selenium 3.0 officially deprecated the Selenium RC API, although it remained available for backward compatibility.
    - **GeckoDriver for Firefox**: Introduced GeckoDriver to support Mozilla's Marionette, a protocol for remote control of Firefox.
    - **W3C WebDriver Standard**: Moved towards compliance with the W3C WebDriver specification, aiming for a standard way of automating browsers.
    - **Improved Stability and Performance**: Continued improvements in stability, performance, and compatibility with modern browsers and web applications.

## Selenium 4.0
- **Release Date**: October 2021
- **Key Features**:
    - **Fully W3C Compliant**: Selenium 4.0 is fully compliant with the W3C WebDriver standard, ensuring a standardized and interoperable way to automate web browsers.
    - **New Browser DevTools Protocols**: Added support for Chrome DevTools and Edge DevTools protocols, allowing for deeper browser interactions such as network interception, capturing performance metrics, and debugging.
    - **Improved Grid**: A revamped Selenium Grid with support for Docker, improved scaling, and easier setup.
    - **Relative Locators**: Introduced relative locators (e.g., find elements near, to the left of, above, below other elements) to simplify locating elements on a page.
    - **Better Documentation and IDE**: Enhanced documentation and a new Selenium IDE for easier creation and management of test scripts.
    - **WebDriver BiDi**: Introduced initial support for bidirectional communication with the browser, enabling more interactive automation scenarios.

These developments reflect the ongoing evolution of Selenium to keep pace with changes in web technologies and the needs of the automation community.




---
## Flash cards section

What are the Selenium suite components?
?
Selenium IDE, Selenium RC, Selenium WebDriver, Selenium Grid

What is the difference between Selenium 2.0 and Selenium 3.0?
?
Selenium 2.0 streamlined creating automated tests for web applications by combining the original Selenium project with the WebDriver project. While Selenium Remote Control (RC) became outdated after the merge, it was still supported for a while to ensure existing tests wouldn’t break.
<!--SR:!2024-07-11,1,230-->

Is Selenium WebDriver and Selenium RC is the same?
?
No, Selenium WebDriver is APIs, which provided a more robust and efficient way to interact with web browsers compared to the older Selenium RC (Remote Control).

In which version does Selenium RC get removed? 
?
Selenium 3.0, but it's remained available for backward compatibility.

W3C WebDriver Standard was introduced in which version?
?
Selenium 3.0 but until to Selenium 4.0 it was become fully W3C WebDriver Standard