# regexp-collection

**专业收集各种 javascript 正则表达式**

### 解析 url 的正则表达式

```
const URL_REG = new RegExp(
    '^([a-z0-9-]+\:)?' +                  //protocol
    '[/]{2}' +                            //slash x 2
    '(?:([^@/:\?]+)(?::([^@/:]+))?@)?' +  //username:password@
    '([^:/?#]+)' +                        //hostname
    '(?:[:]([0-9]+))?' +                  //port
    '([/][^?#;]*)?' +                     //pathname
    '(?:[?]([^#]*))?' +                   //search
    '([#][^?]*)?$'                        //hash
, 'i');

```
* 使用

```
url = url || '';
var matches = url.match(URL_REG);

if (matches) {
    this.protocol = matches[1] || (typeof location === 'object' ? location.protocol : '');
    this.username = matches[2] || '';
    this.password = matches[3] || '';
    this.hostname = matches[4];
    this.port = matches[5] || '';
    this.pathname = matches[6] || '/';
    this.search = matches[7] || '';
    this.hash = matches[8] || '';
    this.origin = this.protocol + '//' + this.host;
} else {
    throw new Error('Parse Error');
}

```