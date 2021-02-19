---
title: "RFC 2397 - The \"data\" URL scheme"
date: 2014-11-26T23:46:55+01:00
source: "https://tools.ietf.org/html/rfc2397"
---

I've still been having way too much fun playing around with [my self-editing data URL "page"][ouroboros], and wound up finding the original proposal for data URLs from the IETF dated August 1998:

> Some applications that use URLs also have a need to embed (small) media type data directly inline. This document defines a new URL scheme that would work like 'immediate addressing'. The URLs are of the form:
>
> ```
> data:[<mediatype>][;base64],<data>
> ```
>
> The `<mediatype>` is an Internet media type specification (with optional parameters.) The appearance of "`;base64`" means that the data is encoded as base64. Without "`;base64`", the data (as a sequence of octets) is represented using ASCII encoding for octets inside the range of safe URL characters and using the standard `%xx` hex encoding of URLs for octets outside that range.  If `<mediatype>` is omitted, it defaults to `text/plain;charset=US-ASCII`.  As a shorthand, "`text/plain`" can be omitted but the charset parameter supplied.

And apparently the idea goes back even further:

> This idea was originally proposed August 1995. Some versions of the
   data URL scheme have been used in the definition of VRML, and a
   version has appeared as part of a proposal for embedded data in HTML.
   Various changes have been made, based on requests, to elide the media
   type, pack the indication of the base64 encoding more tightly, and
   eliminate "quoted printable" as an encoding since it would not easily
   yield valid URLs without additional `%xx` encoding, which itself is
   sufficient. The "data" URL scheme is in use in VRML, new applications
   of HTML, and various commercial products. It is being used for object
   parameters in Java and ActiveX applications.

I kind of love looking at older documents like this about the inner workings of the web. I primarily see them used for inlining images, as [outlined by Chris Coyier](http://css-tricks.com/data-uris/), but the idea of encoding an entire page is just somehow still tripping me out.

Maybe it'll pass.

[ouroboros]:data:text/html;charset=utf-8,%3C!doctype%20html%3E%0A%3Chtml%20lang%3D%22en%22%3E%0A%20%20%3Chead%3E%0A%20%20%20%20%3Cmeta%20charset%3D%22utf-8%22%3E%0A%20%20%20%20%3Ctitle%3EData%20URL%20Ouroboros%3C%2Ftitle%3E%0A%20%20%20%20%3C!--%20via%20notated.org%2C%20based%20on%20https%3A%2F%2Funhosted.org%2Fadventures%2F2%2FAn-unhosted-editor.html%20--%3E%0A%20%20%20%20%3Cscript%20src%3D%22http%3A%2F%2Fcodemirror.net%2Flib%2Fcodemirror.js%22%3E%3C%2Fscript%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22http%3A%2F%2Fcodemirror.net%2Flib%2Fcodemirror.css%22%20%2F%3E%0A%20%20%20%20%3Cscript%20src%3D%22http%3A%2F%2Fcodemirror.net%2Fmode%2Fxml%2Fxml.js%22%3E%3C%2Fscript%3E%0A%20%20%20%20%3Cscript%20src%3D%22http%3A%2F%2Fcodemirror.net%2Fmode%2Fjavascript%2Fjavascript.js%22%3E%3C%2Fscript%3E%0A%20%20%20%20%3Cscript%20src%3D%22http%3A%2F%2Fcodemirror.net%2Fmode%2Fcss%2Fcss.js%22%3E%3C%2Fscript%3E%0A%20%20%20%20%3Cscript%20src%3D%22http%3A%2F%2Fcodemirror.net%2Fmode%2Fhtmlmixed%2Fhtmlmixed.js%22%3E%3C%2Fscript%3E%0A%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20body%20%7B%20background%3A%20%23EEE%3B%20font-family%3A%20sans-serif%3B%20margin%3A%203em%3B%20padding%3A%200%3B%20%7D%0A%20%20%20%20%20%20a%20%7B%20color%3A%20%23C00%3B%20%7D%0A%20%20%20%20%20%20small%20%7B%20color%3A%20%23999%3B%20%7D%0A%20%20%20%20%20%20.CodeMirror%20%7B%20border%3A%201px%20solid%20%23CCC%3B%20height%3A%20auto%3B%20%7D%0A%20%20%20%20%20%20.CodeMirror-scroll%20%7B%20overflow-y%3A%20hidden%3B%20overflow-x%3A%20auto%3B%20%7D%0A%20%20%20%20%3C%2Fstyle%3E%0A%20%20%3C%2Fhead%3E%0A%20%20%3Cbody%3E%0A%20%20%20%20%3Carticle%3E%0A%20%20%20%20%20%20%3Ch1%3EData%20URL%20Ouroboros%3C%2Fh1%3E%0A%20%20%20%20%20%20%3Cp%3ETry%20making%20a%20change%20in%20the%20code%20below%20and%20hitting%20“Save.”%3C%2Fp%3E%0A%20%20%20%20%20%20%3Cp%3E%3Csmall%3EBased%20on%20%3Ca%20href%3D%22https%3A%2F%2Funhosted.org%2Fadventures%2F2%2FAn-unhosted-editor.html%22%3EAn%20unhosted%20editor%3C%2Fa%3E%3C%2Fsmall%3E%3C%2Fp%3E%0A%20%20%20%20%3C%2Farticle%3E%0A%20%20%20%20%3Cdiv%20id%3D%22editor%22%3E%3C%2Fdiv%3E%0A%20%20%20%20%3Cdiv%3E%0A%20%20%20%20%20%20%3Cbutton%20onclick%3D%22save()%22%3ESave%3C%2Fbutton%3E%0A%20%20%20%20%20%20%3Csmall%20id%3D%22filesize%22%3E%3C%2Fsmall%3E%0A%20%20%20%20%3C%2Fdiv%3E%0A%20%20%3C%2Fbody%3E%0A%20%20%3Cscript%3E%0A%20%20%20%20var%20editor%20%3D%20CodeMirror(%20document.getElementById('editor')%2C%20%7B%20lineNumbers%3A%20true%2C%20mode%3A%20'htmlmixed'%2C%20viewportMargin%3A%20Infinity%20%7D)%3B%0A%20%20%20%20editor.setValue(decodeURIComponent(location.href.substring('data%3Atext%2Fhtml%3Bcharset%3Dutf-8%2C'.length)))%3B%0A%20%20%20%20document.getElementById('filesize').innerHTML%20%3D%20Math.round(%20location.href.length%20%2F%201024%20)%20%2B%20'k'%3B%0A%20%20%20%20function%20save()%20%7B%0A%20%20%20%20%20%20location.href%20%3D%20'data%3Atext%2Fhtml%3Bcharset%3Dutf-8%2C'%20%2B%20encodeURIComponent(editor.getValue())%3B%0A%20%20%20%20%7D%0A%20%20%3C%2Fscript%3E%0A%3C%2Fhtml%3E
