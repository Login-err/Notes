```html
<!--cdn引入-->
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
    /*
    *	在vue原型上添加$axios属性
    */
    Vue.prototype.$axios = axios
    const son = {
        template:"<h2></h2>",
        crated(){
            this.$axios.get('url').then((res)=>{
                console.log(res);
            })
        }
    }
    const son = {
        template:"<h2></h2>",
        async crated(){
            const data = await this.$axios.get('url');
        }
    }
    const son = {
        template:"<h2></h2>",
        async crated(){
            const data = await this.$axios.get('url');
        }
    }
	let vm = new Vue({})
</script>

```

