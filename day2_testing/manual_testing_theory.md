##What is manual testing?
Manual testing is when testers execute test cases themselves, observe the results, and decide if the behavior is correct, instead of letting scripts or tools run the tests automatically. It is especially useful for checking user experience, new features, and complex scenarios where human judgment and intuition matter a lot.​

“Manual testing is the process where I manually execute test cases or explore the application to find defects, without using automation tools. It helps me verify functionality and user experience from a real user’s perspective.”

##Functional testing (and Negative testing)
Functional testing
Functional testing checks “Does this feature do what the requirement says?”. You treat the system as a black box: you give inputs and verify outputs match the expected behavior.​

Beginner view: You take each requirement and try it with valid, normal data.

Example: For login, enter correct email and correct password → you should reach the dashboard.

“Functional testing verifies that each feature works according to the specified requirements, for example checking that a user with valid credentials can successfully log in.”

##Negative testing
Negative testing checks “Does the system handle wrong or unexpected input safely?”. You try to break it by giving bad data and weird actions.​

Beginner view: You test with invalid emails, wrong passwords, empty fields, very long text, special characters, etc.

Example: Wrong password should not log in, and should show a clear error message.

“Negative testing focuses on invalid or unexpected inputs to make sure the system doesn’t behave incorrectly or crash, such as ensuring login fails with an incorrect password.”

##UI/UX testing
UI/UX testing checks how the application looks and feels, not just whether it technically works. You focus on layout, readability, alignment, colors, messages, and how easy it is for a user to complete tasks.​

UI (User Interface): Are buttons aligned? Is text readable? Are labels clear?

UX (User Experience): Is the flow logical? Can a new user understand what to do next? Are error messages helpful?

Example:
On the login page, if the error text is tiny grey text at the top, it’s hard to notice; good UX would show a clear red error message near the input field.

“UI/UX testing ensures the application is easy to use, visually correct, and that messages and flows are clear for the user, not just technically functional.”


##Regression testing
Regression testing checks “Did we break anything that used to work?” after a change like a bug fix or new feature. You re-run important older test cases to confirm existing functionalities still behave correctly.​

Example: After adding a ‘Remember Me’ checkbox, you re-test normal login, logout, and password reset to confirm they still work as before.

“Regression testing is re-running previously passed tests after code changes to ensure existing functionality hasn’t been broken.”

##Smoke testing
Smoke testing is a quick, shallow check to see if the build is stable enough for deeper testing.​

Beginner view: You test only the most critical paths (can I open the app? log in? open main pages?). If this fails, there’s no point doing detailed testing yet.

Example: After deployment, you check: app loads, login page opens, login works with a valid user.

“Smoke testing is a fast check of core features to confirm the build is stable and worth testing further.”

##Exploratory testing
Exploratory testing is unscripted, learning-by-doing testing where you don’t follow detailed written test cases but use your knowledge, curiosity, and intuition to find issues. You explore the application, try different paths, combine actions, and see what breaks.​

Beginner view: Click around like a curious user: try unusual flows (e.g., change password while logged in on multiple devices, submit forms multiple times, go back/forward in the browser, etc.).

It’s great for new features, poorly documented areas, or when you want to find “weird” bugs that scripted tests might miss.​

Example:
On a shopping site, you might add items to cart, change quantities many times, remove items, refresh, go back and forward, and see if totals, prices, and states are always correct.

“Exploratory testing is where I simultaneously learn the application, design tests, and execute them on the fly, using my experience and curiosity to uncover unexpected defects that scripted test cases might miss.”
