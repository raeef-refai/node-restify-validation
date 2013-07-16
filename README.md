node-restify-validation
=======================
Validation for REST Services built with [node-restify](https://github.com/mcavage/node-restify) in node.js

[![Build Status](https://travis-ci.org/z0mt3c/node-restify-validation.png)](https://travis-ci.org/z0mt3c/node-restify-validation)
[![Coverage Status](https://coveralls.io/repos/z0mt3c/node-restify-validation/badge.png?branch=master)](https://coveralls.io/r/z0mt3c/node-restify-validation?branch=master)
[![Dependency Status](https://gemnasium.com/z0mt3c/node-restify-validation.png)](https://gemnasium.com/z0mt3c/node-restify-validation)


Simple request validation with node-restify
-------------------------------------------
Goal of this little project is to have the validation rules / schema as close to the route itself as possible on one hand without messing up the logic with further LOCs on the other hand.

Example:

    var server = restify.createServer();
    server.use(restify.queryParser());
    server.use(restifyValidation.validationPlugin( { errorsAsArray: false }));
    
    server.get({url: '/test/:name', validation: {
        name: { isRequired: true, isIn: ['foo','bar'], scope: 'path' },
        status: { isRequired: true, isIn: ['foo','bar'], scope: 'query' },
        email: { isRequired: false, isEmail: true, scope: 'query' },
        age: { isRequired: true, isInt: true, scope: 'query' }
    }}, function (req, res, next) {
        res.send(req.params);
    });
    
    server.listen(8001, function () {
        console.log('%s listening at %s', server.name, server.url);
    });

Use
---
Simply install it through npm

    npm install node-restify-validation


Documentation powered by swagger
--------------------------------
On top of the validation schema the [node-restify-swagger](https://github.com/z0mt3c/node-restify-swagger) library should later-on generate the swagger resources to provide a hands-on documentation. 

Demo project
------------
A simple demo project can be cloned from [node-restify-demo](https://github.com/z0mt3c/node-restify-demo).

Supported validations
---------------------
Powered by [node-validator](https://github.com/chriso/node-validator).

    isRequired
    contains
    equals
    is
    isAfter
    isAlpha
    isAlphanumeric
    isBefore
    isCreditCard
    isDate
    isDecimal
    isDivisibleBy
    isEmail
    isFloat
    isHexColor
    isHexadecimal
    isIP
    isIPNet
    isIPv4
    isIPv6
    isIn
    isInt
    isLowercase
    isNumeric
    isUUID
    isUUIDv3
    isUUIDv4
    isUppercase
    isUrl
    max
    min
    not
    notContains
    notIn
    notRegex
    regex

License
-------

The MIT License (MIT)

Copyright (c) 2013 Timo Behrmann

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

Inspiration
-----------
node-restify-validation was & is inspired by [backbone.validation](https://github.com/thedersen/backbone.validation). 
In terms of validation node-restify-validation makes use of [node-validator](https://github.com/chriso/node-validator).





