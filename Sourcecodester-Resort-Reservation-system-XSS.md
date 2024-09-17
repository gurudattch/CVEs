# Reflected XSS vulnerability was discovered in Sourcecodester's Resort Reservation System - PHP 1.0 (toview)
---

---
Affected Project: Sourcecodester's Resort Reservation System

Official Website: [Sourcecodester's Resort Reservation System]()

Version: 1.0
---
## CVE-2024-XXXX
---

Vulnerability Discription
---
The manage_fee.php id not properly sentized for Javascript filter and the paramter **toview's **
 value taking by a conditional opration as a argument resultant the code executing Javascript 

Releted Code: manage_fee.php

```
<script>
    $(function(){
        $('#fee-form').submit(function(e){
            e.preventDefault();
            $('.pop_msg').remove()
            var _this = $(this)
            var _el = $('<div>')
                _el.addClass('pop_msg')
            start_loader()
            $.ajax({
                url:'./Master.php?a=save_fee',
                method:'POST',
                data:$(this).serialize(),
                dataType:'JSON',
                error:err=>{
                    console.log(err)
                    _el.addClass('alert alert-danger')
                    _el.text("An error occurred.")
                    _this.prepend(_el)
                    _el.show('slow')
                    end_loader();
                    $('html, body').scrollTop(0)
                },
                success:function(resp){
                    if(resp.status == 'success'){
                        if('HelloHacker' == ""){ //XSS Vulnerable Code
                            location.replace("./?page=fees");
                        }else{
                            location.replace("./?page=view_fee&id=");
                        }
                    }else{
                        _el.addClass('alert alert-danger')
                    }
                    _el.text(resp.msg)

                    _el.hide()
                    _this.prepend(_el)
                    _el.show('slow')
                    $('html, body').scrollTop(0)
                    end_loader()
                }
            })
        })
    })
</script>
```

![image](https://github.com/gurudattch/CVEs/blob/main/assets/24.png)

---
http://192.168.16.161/manage_fee.php?toview=')</script><script>alert()</script>

![image1](https://github.com/gurudattch/CVEs/blob/main/assets/23.png)

---
