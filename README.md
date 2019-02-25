#  ## vue简单的搜索查询
```
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<!-- 生产环境版本，优化了尺寸和速度 -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
<style type="text/css">
	ul{
		list-style: none;
		
	}
	ul li{
		width:40%;
		float: left;
	}
</style>
</head>
<body>
	<div id="app">
		<input v-model="key" type="text">
		<ul v-for="item in search">
			<li>{{item.names}}</li>
			<li>{{item.tel}}</li>
		</ul>
	</div>
</body>
<script>
	var vue = new Vue({
		el:'#app',
		data(){
			return{
				key:'',
				bodys:'',
				search:[]
			}
		},
		watch:{
			key:function(newValue,oldValue) {
				var that = this;
				
				if(newValue!=oldValue){
					var arrs=[];
					for(var i=0;i<that.bodys.length;i++){
						if(that.bodys[i].tel.indexOf(newValue)==0){
							arrs.push(that.bodys[i]);
							that.search=arrs;
							console.log(that.search);
						}
					}		
				}	
			}
		},
		mounted(){
			this.init();
			this.search=this.bodys
		},
		methods:{
			init(){
				this.bodys=[{'names':'熊？璇','tel':'15243623738'},
					{'names':'惠元','tel':'18569498484'},
					{'names':'老姨','tel':'13963317597'},
					{'names':'电信安装','tel':'13348617628'},
					{'names':'左建维','tel':'18390807665'},
					{'names':'周建琳','tel':'1828019409'}]
			}
		}
	})
</script>
</html>
```
