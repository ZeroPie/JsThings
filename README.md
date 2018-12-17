# Javascript-Reference
Just a Reference to look into

### Computed Property Names in Objects:

<pre> 
const obj = {
    [action.name]: action.payload
};
</pre>



DONT: Implicitly create a Global as a result of assigning to a variable that was never declared:
Fix: dont do it or 'use strict' => reference Error is then thrown

After Compile at Runtime 
<pre>
function wat() {
    lulz = 'imglobalnow lulz'
}
</pre>
