Explanation:
The issue in your JavaScript code lies in how you're selecting the <body> element. You're using document.querySelectorAll('body'), which returns a NodeList (an array-like object) containing all <body> elements. Since there's only one <body> element in a valid HTML document, this NodeList contains a single element. However, when you attempt to set body.style.backgroundColor, you're trying to access the style property directly on the NodeList, which doesn't exist, leading to an error.

Correction:

Replace document.querySelectorAll('body') with document.querySelector('body'). The querySelector method returns the first matching element, which is appropriate here since there's only one <body> element.