# Sprint rules:

Please complete the story point addition and task breakdown for your main story if anyone has not yet been added.  Jira should be perfect before starting the sprint.
<br>
 * Branch creation should be discussed with your own team members to avoid duplicate branches.

 * Take the latest from main/dev and create a branch like dev-1000 (jira ticket number)
 
 * Every push from your local branch to the main branch, which means into dev, should be through a Pull Request.
 
 * Add reviewers and verify it was reviewed on time and deployed.
 
 * Any doubts in anything contact your own team leads.
 
 * Auto generated files should not be committed or pushed to the local or cloud.
 
 * If you are adding any kind of library files or something new, please have a call or discuss it with your leads and inform us here to avoid last-minute struggles in case of deployment or build issues.
 
 * Tasks should be completed on time. Concentrate on the task delivery on time.

 ---

 ### Standard Coding checklist for Angular:

1. Brain storming is done and approach is documented for the task and work scope is identified.

2. Use const and let (Yes/No/Reason if NA)

3. Never use Wrapper classes in UI, always use primitive classes

4. Use single quotes ' ' for strings.

5. Use `===`  and  `!==` over `==` and `!=`

6. Use template literal instead of string concatenation

7. Use dot notation to access the property and use optional chaining. Use bracket notation [] when accessing properties with a variable or properties that spans multiple words.

8. Avoid using _(underscore) in the method names

9. Use semicolon; after end of the line

10. Always use braces {} during if…else conditions

11. In a single line code should not excess more than 100 characters

12. `'any'` type is only used wherever must to have else proper type is used

13. Comments are provided for each functionality properly. Also, methods and variable names should be as per the functionality of the code.

```js
  /**
   *
   * @param refreshGrid flag to refresh the grid based on `refreshGrid`
   * @description method close the opened modal.
   */

```

14. ng-deep is only use if it is the only option to achieve the expected change 

15. Hardcoded strings/numbers are not used in the code and constants/variables/Enums are created instead

16. Throughout the code-naming convention of variable, methods and constants are maintained

17. Any unused variable is removed from the file and there is no duplicate code.

---

