# Modelica OSS Library Testing Analysis
This small repository contains a rough overview as of summer 2023 over testing solutions used in open source Modelica library developments. I started to compile [this list](/modelica-libs-testing-analysis.csv) to get an idea over existing 
- test automation
- continuous integration workflows
- regression testing solutions
used by the open source community in Modelica library development. 

## Data source
As a data source I used the repositories in the repository collection [Modelica 3rd-party libraries](https://github.com/orgs/modelica-3rdparty/repositories). I only considered repositories that had at least one commit since 2019. 

## Analysis methodolody and disclaimer
To my knowledge, in Modelica library development there is no *universally adopted* practice yet on where to put and how to formulate
- Modelica library tests
- Test automation for library tests
- CI/CD workflows
- regression tests.

Therefore, I had to resort to manually looking through all the repositories from the above collection 
- using keyword searches for "test" and "regression"
- searching for `.github` or `.gitlab` folders or travis files with workflow automation definitions
- walking through the source folders in order to discover testing solutions that are not obvious to spot or locate.

This process is entirely manual and unfortunately error-prone. Hence, I might have overlooked or not correctly recognized some testing solutions, and some findings in the listing might be incorrect. Please open an issue to report mistakes so I can correct the listing if necessary. 

## Categories
For every repository, I looked at four criteria
- **C0: Has library tests in sources**
  - Meaning: There exist dedicated executable tests that demonstrate or check the correct working of the library or its elements. 
  - Examples: Modelica-native unit tests formulated in `.mo` or files.
- **C1: Has automated tests in sources**
  - Meaning: There is some sort of mechanism in the repository that can be used to automate test execution (library tests, syntax checking,...). This does not imply that the tests are actually automatically run. 
  - Examples: A `.mos` script that runs a test battery of `.mo` files.
- **C2: Has tests integrated into a CI pipeline**
  - Meaning: There is a workflow for a continuous integration (CI) pipeline that automatically runs tests. 
  - Example: [moparser syntax checking](https://github.com/modelica-tools/ModelicaSyntaxChecker) in a GitLab CI/CD workflow, or execution of test batteries defined in `.mos` files in a GitHub Action.
- **C3: Has regression tests in sources**
  - Meaning: There is some definition of regression tests and a means to execute them. The regression does not have to be automatically executed. 
  - Example: A regression test definition in a `.py` file using the [BuildingsPy Regression Test](https://github.com/lbl-srg/BuildingsPy).

## Remarks
1. The criteria definition is not perfect and does not claim to be stricly well-defined. It is meant to give an indication. 
2. It is perfectly possible that a repository has no library tests according to criterion C0, but tests in a CI pipeline according to C2. E.g. when moparser is used for syntax checking, but no test models or regression tests have been defined. 
3. Besides recurring popular testing solutions like for instance
  - [BuildingsPy Regression Test](https://github.com/lbl-srg/BuildingsPy),
  - [moparser syntax checking](https://github.com/modelica-tools/ModelicaSyntaxChecker)
  there is a wide variety of sometimes ad hoc implemented testing solutions. The listing states such findings in the Remarks column.
4. The difference between Modelica native tests like in criterion C0 and the usually included Examples packages is often not clear to me. In some cases it appears to be the naming that makes the difference. Thus C0 can be rather fragile as a criterion. 

## Update history
- Initial analysis: June 13, 2023
- Update: August 14, 2023

## Author
Dr. Philipp Emanuel Stelzig
