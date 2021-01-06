# Here are the summary notes
## Overview of how it works
Touch Id authentication works on using a new web standard called Web Authentication API that has been implemented in certain browsers (see supprted devices below).  the Web Authentication Standard uses a public-private key as a credential to authenticate users onto a site.  When a user first registers with a site the browser will create a public-private key pair.  The public key is then transmitted to ther server (during registration) and is stored on the server (i.e. database).  When the user attempts to login into the site again, the browser will submit the public key to the server and it will check to ensure that it is valid.   

## Initial findings
I did some investigation on how to use the touch id with the login and it seems possible; however, there are a couple of caviates.  The first thing is that it is not fully supported across all browsers (see the list below of supprted browsers).  The second is that I have not seen a lot of production ready implementations in place yet (i.e. specifically for touch id); however, I have seen multiple open source implementations that we could leverage if we wanted to implement out own.  The implementation will require both some UI changes as well as some changes to the downstream

## Supported 
The following is an updated list of the different browsers that current support Touch ID as well as other secure log in mechanisms

https://simplewebauthn.dev/docs/advanced/supported-devices

## Implementation Notes

### UI Changes
To take advantage of the UI changes, it rely's on browsers that support the Web Authentication API.  From some of the code that I have seen it is possible to detect which browsers support this feature and it should be straight forward for us to enable this for certain browsers.



## Supported libraries