Ansible lookup("template") test
===============================

Just execute the ``./site.yml`` playbook to run the test.

Output on Ansible v1.9+
-----------------------

::

    PLAY [Test template lookup] *************************************************** 
    
    GATHERING FACTS *************************************************************** 
    ok: [localhost]
    
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

Output on Ansible v2
--------------------

::

    PLAY [Test template lookup] ****************************************************
    
    TASK [setup] *******************************************************************
    ok: [localhost]
    
    TASK [lookup-test : Display the list] ******************************************
    fatal: [localhost]: FAILED! => {"failed": true, "msg": "ERROR! the template file lookup/variable.j2 could not be found for the lookup"}

