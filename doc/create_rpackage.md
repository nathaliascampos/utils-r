# Creating an R package

### Step 0: Packages you will need

The packages you will need to create a package are devtools and roxygen2.

``` r
install.packages("devtools")
library("devtools")
install.packages("roxygen")
library(roxygen2)
```

### Step 1: Create your package directory

``` r
setwd("parent_directory")
devtools::create("my_package")
```

### Step 2: Create a function

- Create a function; 
- Document the function using `roxygen2`. 

---

## Document Workflow 

Use roxygen to document a package. 

Document your functions with Ctrl/Cmd + Shift + D or [`devtools::document()`](https://www.rdocumentation.org/packages/devtools/versions/2.4.2/topics/document). 

```
> devtools::document()
Updating packageName documentation
Loading packageName
Writing NAMESPACE
Writing NAMESPACE
Documentation completed
```

---

## Check Workflow

Automatically builds and checks a source package, using all known best practices. 

Check your package with Ctrl/Cmd + Shift + E or [`devtools::check()`](https://www.rdocumentation.org/packages/devtools/versions/2.4.2/topics/check).

Ps.: `check` function has a `document` parameter. By default (NULL) will document if your installed roxygen2 version matches the version declared in the DESCRIPTION file. Use `TRUE` or `FALSE` to override the default.

```
> devtools::check()
Updating packageName documentation
Loading packageName
Writing NAMESPACE
Writing NAMESPACE
── Building ────────────────────────────────────────── packageName ──
Setting env vars:
• CFLAGS    : -Wall -pedantic -fdiagnostics-color=always
• CXXFLAGS  : -Wall -pedantic -fdiagnostics-color=always
• CXX11FLAGS: -Wall -pedantic -fdiagnostics-color=always
────────────────────────────────────────────────────────────────────
✓  checking for file ‘/home/nathalia/Documents/R/packageName/DESCRIPTION’ ...
─  preparing ‘packageName’:
✓  checking DESCRIPTION meta-information ...
─  checking for LF line-endings in source and make files and shell scripts
─  checking for empty or unneeded directories
─  building ‘packageName_0.1.0.tar.gz’

...

── R CMD check results ────────────────────── packageName 0.1.0 ────
Duration: 14.9s

0 errors ✓ | 0 warnings ✓ | 0 notes ✓
```

---

## Test Workflow 

Run [`usethis::use_testthat()`](https://www.rdocumentation.org/packages/usethis/versions/2.0.1/topics/use_testthat) to:
- Create a `testes/testthat` directory; 
- Add testthat to the `Suggets` field in the `DESCRIPTION`; 
- Creates a file `tests/testthat.R` that runs all your tests when R CMD check runs.

```
> usethis::use_testthat()
✓ Setting active project to '/home/nathalia/Documents/R/packageName'
✓ Adding 'testthat' to Suggests field in DESCRIPTION
✓ Setting Config/testthat/edition field in DESCRIPTION to '3'
✓ Creating 'tests/testthat/'
✓ Writing 'tests/testthat.R'
● Call `use_test()` to initialize a basic test file and open it for editing.
```

Once you’re set up the workflow is simple:
- Modify your code or tests.
- Test your package with Ctrl/Cmd + Shift + T or [`devtools::test()`](https://www.rdocumentation.org/packages/devtools/versions/2.4.2/topics/test).
- Repeat until all tests pass.


----
### References: 

[Writing an R package from scratch](https://hilaryparker.com/2014/04/29/writing-an-r-package-from-scratch/)
