###析构
```
const {dispatch, navigator} = this.props
var left = this.props.left;
var props = {};

Object.keys(this.props).forEach(function(key, index){
if (key !== 'left') {
    props[key] = this.props[key];
}
}, this);
```


http://stackoverflow.com/questions/28534344/javascript-var-left-props-this-props
