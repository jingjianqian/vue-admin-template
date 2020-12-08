<template>
	<div class="app-container">
		<el-button :loading="downloadLoading"
			type="primary" 
			icon="el-icon-document" @click="handlDownload">
		新增	
		</el-button>
		<el-table 
			ref="multipleTable"
			v-loading="listLoading"
			:data="list"
			element-loading-text="加载中"
			border fit hightlight-current-now>
			<el-table-column label="序号" align="center" width="95">
				<template slot-scope="scope">
					{{ scope.$index+1 }}
				</template>
			</el-table-column>
			<el-table-column label="角色名称" align="center">
				<template slot-scope="scope">
					{{scope.row.role_name}}
				</template>
			</el-table-column>
			<el-table-column label="角色任务" align="center">
				<template slot-scope="scope">
					{{scope}}
				</template>
			</el-table-column>
			<el-table-column label="操作" align="center">
				<template slot-scope="scope">
					123213
				</template>
			</el-table-column>
		</el-table>
	</div>
</template>
<script>
	import { getList } from '@/api/roleManage'
	export default{
		name:"RoleManager",
		data(){
			return{
				list:null,
				listLoading:true,
				downloadLoading:false
			}
		},
		created(){
			this.fetchData() 
		},
		methods:{
			fetchData(){
				this.listLoading=false
				getList(this.listQuery).then(response =>{
					console.log(response);
					this.list = response.data.data
					this.listLoading = false
				})

			},
			handlDownload(){
				this.downloadLoading = true;
				alert("TODO add!!!");
			}
		}
	}
</script>