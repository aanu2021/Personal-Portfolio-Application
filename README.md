### Requirements

- Any Editor (preferably Visual Studio Code)
- Local git setup 


### Cloning locally

- Clone the repository 

```console
    git clone https://github.com/aanu2021/Personal-Portfolio-Application.git
```

### Running locally

- Open in Visual Studio Code.
- Install Live server extension.
- Run Live server.
- Your application will be up and running fine.


### Instructions

- We have two files, <b>index.html</b>, and <b>styles.css</b>.
- Also there is a <b>script</b> tag present at the bottom of the <b>index.html</b> file, under which the main logic is placed.
- On the navbar, there is a <b>button</b> to run the given tests.
- After running all the tests, it will automatically generate a <b>.txt</b> file, containing the <b>verdict</b> of the tests.


### Solution script

```
<script>
    document.addEventListener('DOMContentLoaded', function () {
        const validationResults = document.getElementById('validation-results');
        const runTestsButton = document.getElementById('run-tests-btn');

        runTestsButton.addEventListener('click', function () {
            runTests(validationResults);
        });

        function runTests(validationResults) {
            let errorCount = 0;
            let testResults = '';

            // 1. Check for the Welcome section with an id of welcome-section
            const welcomeSection = document.getElementById('welcome-section');
            if (!welcomeSection) {
                testResults += 'Error: Your portfolio should have a "Welcome" section with an id of welcome-section !\n';
                errorCount++;
            }
            else {
                // 2. Check if #welcome-section contains an h1 element
                const welcomeHeading = welcomeSection.querySelector('h1');
                if (!welcomeHeading) {
                    testResults += 'Error: Your #welcome-section element should contain an h1 element !\n';
                    errorCount++;
                }
                else {
                    // 3. Check for empty h1 elements within #welcome-section element
                    if (welcomeHeading.innerText.trim() === '') {
                        testResults += 'Error: You should not have any empty h1 elements within #welcome-section element !\n';
                        errorCount++;
                    }
                }
            }

            // 4. Check for Projects section with an id of projects
            const projectsSection = document.getElementById('projects');
            if (!projectsSection) {
                testResults += 'Error: You should have a "Projects" section with an id of projects !\n';
                errorCount++;
            }

            // 5. Check if portfolio contains at least one element with a class of project-tile
            const projectTiles = document.querySelectorAll('.project-title');
            if (projectTiles.length === 0) {
                testResults += 'Error: Your portfolio should contain at least one element with a class of project-title !\n';
                errorCount++;
            }

            if (projectsSection) {
                // 6. Check if #projects element contains at least one a element
                const projectLinks = projectsSection.querySelectorAll('a');
                if (projectLinks.length === 0) {
                    testResults += 'Error: Your #projects element should contain at least one a element !\n';
                    errorCount++;
                }
            }

            // 7. Check for navbar with an id of navbar
            const navbar = document.getElementById('navbar');
            if (!navbar) {
                testResults += 'Error: Your portfolio should have a navbar with an id of navbar !\n';
                errorCount++;
            }
            else {
                // 8. Check if #navbar element contains at least one a element whose href attribute starts with #
                const navbarLinks = navbar.querySelectorAll('a[href^="#"]');
                if (navbarLinks.length === 0) {
                    testResults += 'Error: Your #navbar element should contain at least one a element whose href attribute starts with # !\n';
                    errorCount++;
                }
            }

            // 9. Check for an a element with an id of profile-link
            const profileLink = document.getElementById('profile-link');
            if (!profileLink) {
                testResults += 'Error: Your portfolio should have an a element with an id of profile-link!\n';
                errorCount++;
            }
            else {
                // 10. Check if #profile-link element has a target attribute of _blank
                if (profileLink.getAttribute('target') !== '_blank') {
                    testResults += 'Error: Your #profile-link element should have a target attribute of _blank !\n';
                    errorCount++;
                }
            }

            // 11. Check if portfolio uses at least one media query
            const stylesheets = document.styleSheets;
            let hasMediaQuery = false;
            for (let i = 0; i < stylesheets.length; i++) {
                const stylesheet = stylesheets[i];
                const rules = stylesheet.cssRules || stylesheet.rules;
                for (let j = 0; j < rules.length; j++) {
                    const rule = rules[j];
                    if (rule.type === CSSRule.MEDIA_RULE) {
                        hasMediaQuery = true;
                        break;
                    }
                }
                if (hasMediaQuery) {
                    break;
                }
            }
            if (!hasMediaQuery) {
                testResults += 'Error: Your portfolio should use at least one media query !\n';
                errorCount++;
            }

            // 12. Check if #navbar element is always at the top of the viewport
            if (navbar) {
                const navbarRect = navbar.getBoundingClientRect();
                if (navbarRect.top !== 0) {
                    testResults += 'Error: Your #navbar element should always be at the top of the viewport !\n';
                    errorCount++;
                }
            }

            // Display overall validation result
            if (errorCount === 0) {
                testResults += 'All checks passed. Portfolio validation complete.\n';
            } else {
                testResults += 'Validation completed with ' + errorCount + ' error(s).\n';
            }

            // Output test results to the validation-results div
            validationResults.textContent = testResults;

            // Generate text file with test results
            const blob = new Blob([testResults], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'portfolio_validation_results.txt';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        }
    });
</script>

```


### User Interface 

![image](https://github.com/aanu2021/Personal-Portfolio-Application/assets/91496248/f4d5bda5-3467-4b30-ac55-765754649769)

![image](https://github.com/aanu2021/Personal-Portfolio-Application/assets/91496248/845e5b0d-f422-4f64-824f-1629c67506f5)

![image](https://github.com/aanu2021/Personal-Portfolio-Application/assets/91496248/94e8a8ad-b758-4d95-80ee-bd66556ffed4)

![image](https://github.com/aanu2021/Personal-Portfolio-Application/assets/91496248/53bcb23b-f582-4ac8-ab47-d313f13ab156)


### Sample .txt files (test case verdicts)

![image](https://github.com/aanu2021/Personal-Portfolio-Application/assets/91496248/6721b361-cfb9-4142-9685-05a46afbf73a)

![image](https://github.com/aanu2021/Personal-Portfolio-Application/assets/91496248/e51b56c5-3a31-4096-893e-a7f9d4be85df)

