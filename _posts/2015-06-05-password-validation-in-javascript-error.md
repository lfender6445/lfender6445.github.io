---
layout: post
title: "Password Validation in JavaScript Error"
description: ""
category:
tags: []
---

Password Validation in JavaScript Error


I am having trouble with my simple password validations.

These are the things that validation does

- check if password is less than 8 characters
- check if it is more than 15 characters
- check if new password and retyped are mismatched

The form submits when two passwords are matched even if **less than or greater than the validations**

Please see my code:

    function on_submit(dest) {
    
    
  var objForm = document.LogonForm;
  var strMissingInfo = "";
    
    
  if (dest == 'logon') {
    
    
      if (objForm.current.value != "") {
    
    
          if (objForm.new1.value.length < 8 || objForm.new1.value.length > 15) {
              strMissingInfo += "\n Password must be 8 to 15 characters long";
    
    
          } else if (objForm.retype.value != objForm.new1.value) {
              strMissingInfo += "\n Password mismatch!";
    
    
          }
    
    
          if (strMissingInfo != "") {
              alert(strMissingInfo);
    
    
          } else {
              alert(strMissingInfo);
              objForm.action.value = dest;
              objForm.submit();
          }
      }
  }
    }

--- HTML Part

    <input type="password" id="current" name="current"
                              onKeyPress="return isNumberKey(event)" style="width: 180px"
                              tabindex="1" required/>
    
    
    <input type="password" id="new1" name="new1"
                              onKeyPress="return isNumberKey(event)" style="width: 180px"
                              tabindex="2" required />
    
    
    <input type="password" id="retype" name="retype"
                              onKeyPress="return isNumberKey(event)" style="width: 180px"
                              tabindex="3" required />
    
    
    <a href="javascript:;">
                  <input id="logonButton" class="submit"
                      type="submit" name="Submit" value="Confirm" tabindex="4"
                      onclick="on_submit('logon')" />
                  </a>


--------------------------------------- 
if you want the form to fail on submission try returning false when validation fails.

    if (strMissingInfo != "") {
          alert(strMissingInfo);
          return false;
      }


