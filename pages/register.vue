<template>
  <div/>
</template>
<script>
export default {
    methods:{
        sendMsg(){
            const self =this;
            let namePass
            let emailPass
            if(self.timerid){
                return false
            }
            thiS.$refs['ruleForm'].validateField('name',(valid)=>{
                namePass = valid
            })
            self.statusMsg=''
            if(namePass){
                return false
            }
            thiS.$refs['ruleForm'].validateField('email',(valid)=>{
                emailPass = valid
            })
            if(!namePass&&!emailPass){
                self.axios.post('/users/verity',{
                    username:encodeURIComponent(self.ruleForm.name),
                    email:self.ruleForm.email
                }).then(({status,data})=>{
                    if(status===200&&data&&data.code===0){
                        let count =60;
                        self.statusMsg=`验证码已发送,剩余${count--}秒`
                        self.timerid = setInterval(function(){
                            self.statusMsg=`验证码已发送,剩余${count--}秒`
                            if(count===0){
                                clearInterval(self.timerid)
                            }
                        },1000)
                    }else{
                        self.statusMsg =  data.msg
                    }
                })
            }
        },
         
    }
}
</script>

