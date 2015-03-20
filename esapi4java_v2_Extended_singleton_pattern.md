While ESAPI security control reference implementations may perform the security checks and result in the security effects required by your organization and/or application, there may be a need to minimize the need for developers to understand how to call ESAPI functions with the parameters required by your organization and/or application. Availability of training may be an issue, for example. Another example would be to facilitate enforcing a coding standard.

The “extended” singleton pattern refers to the replacement of security control reference implementations with your own implementations and the addition/modification/subtraction of corresponding security control interfaces.

For example:<todo: replace PHP with Java>
```
...
require_once dirname(__FILE__) . '/../Validator.php';
...
//reference implementation
class DefaultValidator implements Validator {
...
//not defined in Validator interface
function isValidEmployeeID($eid) {
...
```
Developers would call ESAPI in this example as follows:
```
...
$ESAPI = new ESAPI();
$validator = ESAPI::getValidator();
$validator->isValidEmployeeID(1234);
...
```

The UML for the above example is in the figure below.

Figure 3: Extended Singleton Pattern Example <todo: picture>

Pros of taking this approach are the lessening of the need for developers to understand how to call ESAPI functions with the specific parameters required by your organization and/or application. Pros also include minimizing or eliminating the ability for developers to call ESAPI functions that deviate from your organization’s and/or application’s policies.

Cons result from the tight coupling between ESAPI and your own implementations: you will need to maintain both the modified security control reference implementations and the modified security control interfaces (as new versions of ESAPI are released over time).