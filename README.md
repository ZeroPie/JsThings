# Javascript-Reference
Just a Reference to look into

### Computed Property Names in Objects:

<pre> 
const obj = {
    [action.name]: action.payload
};
</pre>



DONT: Implicitly create a Global as a result of assigning to a variable that was never declared:

After Compile at Runtime 
<pre>
function wat() {
    lulz = 'imglobalnow lulz'
}
</pre>
