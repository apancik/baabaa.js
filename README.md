# Baabaa.js

Baabaa.js is a client-side A/B testing library using Google Analytics (Universal Analytics) to track the results.

It is compact (500 bytes when minified), framework agnostic, and simple to understand.

## Installation

### 1. Create custom dimension in Google Analytics

Sign in to your Google Analytics account. On Property that you have edit permissions for go to Admin > Custom Definitions > Create new dimension ([?](https://support.google.com/analytics/answer/2709829?hl=en)). 

Set

Name:
> "A/B Experiment"

*Can be any name you want*

Scope:
> "User"

*the dimension is then added to the current and future sessions from that visitor to provide consistent view of the variant*

Active:

> "True"

Note down the dimension id displayed on the next screen.

### 2. Include baabaa.js

Include baabaa.js in your code

    <script src="/baabaa.js"></script>

Just after including Google Analytics Universal Analytics code before actually running ````pageview```` event include the experiments definition and run baabaa.js using the following code

    var experiments = {
        experiment1: [
            {
                name: "variant1",
                action: function () {
                    console.log("variant1");
                }
            },
            {
                name: "variant2",
                action: function () {
                    console.log("variant2");
                }
            }
        ]
    };

    baabaa.run(ga, "dimension1", experiments);

Don’t forget to use your dimension id from the step 1 instead of "dimension1" in the example.

Actions are plain javascript functions and so they can be used in tandem with your favourite DOM manipulation library such as jQuery to modify the page. If you wish to run a control variant in your test just use an empty function.

### 3. Run the experiment and see the results

To measure the performance of your tests go to Reporting > Audience > Custom > User defined > and use the dimension created in step 1 to slice the data.

Before drawing conclusions make sure you read about A/B testing and calculate the confidence levels using for example http://www.evanmiller.org/ab-testing/

## License

Baabaa.js is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.

In jurisdictions that recognize copyright laws, the author or authors of this software dedicate any and all copyright interest in the software to the public domain. We make this dedication for the benefit of the public at large and to the detriment of our heirs and successors. We intend this dedication to be an overt act of relinquishment in perpetuity of all present and future rights to this software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
