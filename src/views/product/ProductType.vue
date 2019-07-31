<template>
	<section>
		<el-row>
			<el-col class="left-conainer" :span="8">
				<!--树-->
				<el-tree :data="productTypes" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
			</el-col>
			<el-col class="righter-conainer" :span="16">

			</el-col>
		</el-row>
	</section>
</template>

<script>
	export default {
        data() {
            return {
                productTypes: [],
                defaultProps: {
                    children: 'children',
                    label: 'name'
                }
            };
        },
        methods: {
            handleNodeClick(data) {
                console.log(data);
            },
            //加载类型数据
            loadProductType(){
                this.$http.get("/product/productType/list")
                    .then(res=>{
                        let data = res.data;
                        this.productTypes = data;
                    })
            }
        },
        mounted(){
            this.loadProductType();
        }
	}

</script>
.left-conainer{
	height: 500px;
	border:1px solid #d9d9d9;
}
.righter-conainer{
	height: 500px;
	border:1px solid #d9d9d9;
	border-left:none
}
<style scoped>

</style>