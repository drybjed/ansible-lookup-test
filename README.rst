Ansible lookup("template") test
===============================

Just execute the ``./site.yml`` playbook to run the test.

Output on Ansible v1.9+
-----------------------

::

   PLAY [Test template lookup] *************************************************** 
   
   GATHERING FACTS *************************************************************** 
   ok: [localhost]
   
   TASK: [lookup-test | Register the output] ************************************* 
   ok: [localhost]
   
   TASK: [lookup-test | Show the output] ***************************************** 
   ok: [localhost] => {
       "var": {
           "debug_variable": "  - 'The one is surrounded'\n  - 'The two is surrounded'\n  - 'The three is surrounded'\n"
       }
   }
   
   TASK: [lookup-test | Display the list] **************************************** 
   ok: [localhost] => (item=The one is surrounded) => {
       "item": "The one is surrounded", 
       "msg": "The one is surrounded"
   }
   ok: [localhost] => (item=The two is surrounded) => {
       "item": "The two is surrounded", 
       "msg": "The two is surrounded"
   }
   ok: [localhost] => (item=The three is surrounded) => {
       "item": "The three is surrounded", 
       "msg": "The three is surrounded"
   }
   
   TASK: [lookup-test | Display the static list] ********************************* 
   ok: [localhost] => (item=aaa) => {
       "item": "aaa", 
       "msg": "aaa"
   }
   ok: [localhost] => (item=bbb) => {
       "item": "bbb", 
       "msg": "bbb"
   }


Output on Ansible v2
--------------------

::

    PLAY [Test template lookup] ****************************************************
    
    TASK [setup] *******************************************************************
    ok: [localhost]
    
    TASK [lookup-test : Register the output] ***************************************
    ok: [localhost]
    
    TASK [lookup-test : Show the output] *******************************************
    ok: [localhost] => {
        "changed": false, 
        "debug_variable": "  - 'The one is surrounded'\n  - 'The two is surrounded'\n  - 'The three is surrounded'\n"
    }
    
    TASK [lookup-test : Display the list] ******************************************
    fatal: [localhost]: FAILED! => {"failed": true, "msg": "ERROR! an unexpected type error occurred. Error was expected string or buffer"}
    ...ignoring
    
    TASK [lookup-test : Display the static list] ***********************************
    fatal: [localhost]: FAILED! => {"failed": true, "msg": "ERROR! an unexpected type error occurred. Error was must be convertible to a buffer, not UnsafeProxy(str)"}
    ...ignoring

