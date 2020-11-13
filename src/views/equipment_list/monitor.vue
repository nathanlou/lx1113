<template>
	<div style="width: 95%;margin-left: 1.5%;margin-top: 1%;color: gray;">
		<div class="msg_con">
			<div style="display: flex;width: 50%;"></div>
			<div class="bigtitle" style="text-align: center;margin-bottom: 2%;margin-top: 1%;">设备信息</div>
			<div style="display: flex;height: 2.8rem;line-height: 2.8rem;border: 0.04rem solid #f4f4f4;">
				<div style="display: flex;width: 50%;">
					<div class="label">企业：</div>
					<div style="margin-left: 0.9375rem;">潜合自动化</div>
				</div>
				<div style="display: flex;width: 50%;">
					<div class="label">设备编号：</div>
					<div style="margin-left: 0.9375rem;">QHW001G210290201</div>
				</div>
			</div>
			<div style="display: flex;height: 2.8rem;line-height: 2.8rem;border: 0.04rem solid #f4f4f4;">
				<div style="display: flex;width: 50%;">
					<div class="label">内部编号：</div>
					<div style="margin-left: 0.9375rem;">qh001</div>
				</div>
				<div style="display: flex;width: 50%;">
					<div class="label">SIM卡号：</div>
					<div style="margin-left: 0.9375rem;">14445415215  <span style="color: dodgerblue;">  正常</span></div>
				</div>
			</div>
			<div style="display: flex;height: 2.8rem;line-height: 2.8rem;border: 0.04rem solid #f4f4f4;">
				<div style="display: flex;width: 50%;">
					<div class="label">负责人：</div>
					<div style="margin-left: 0.9375rem;">杨总</div>
				</div>
				<div style="display: flex;width: 50%;">
					<div class="label">联系电话：</div>
					<div style="margin-left: 0.9375rem;">13800000000</div>
				</div>
			</div>
			<div style="display: flex;height: 2.8rem;line-height: 2.8rem;border: 0.04rem solid #f4f4f4;">
				<div style="display: flex;width: 50%;">
					<div class="label">设备种类：</div>
					<div style="margin-left: 0.9375rem;">YLY1</div>
				</div>
				<div style="display: flex;width: 50%;">
					<div class="label">设备型号：</div>
					<div style="margin-left: 0.9375rem;">1型</div>
				</div>
			</div>
			<div style="display: flex;height: 2.8rem;line-height: 2.8rem;border: 0.04rem solid #f4f4f4;">
				<div style="display: flex;width: 50%;">
					<div class="label">安装日期：</div>
					<div style="margin-left: 0.9375rem;">2020-05-07</div>
				</div>
				<div style="display: flex;width: 50%;">
					<div class="label">到期日期：</div>
					<div style="margin-left: 0.9375rem;">2021-05-07</div>
				</div>
			</div>
			<div style="display: flex;height: 2.8rem;line-height: 2.8rem;border: 0.04rem solid #f4f4f4;">
				<div style="display: flex;width: 50%;">
					<div class="label">当前地址：</div>
					<div style="margin-left: 0.9375rem;">新乡火炬园</div>
				</div>
				<div style="display: flex;width: 50%;">
					<div class="label">通讯时间：</div>
					<div style="margin-left: 0.9375rem;">2021-05-07 06:05:45</div>
				</div>
			</div>
		</div>
		<div class="cp_msg" :style="backgroundDiv">
			<div style="width: 45%;" v-for="(item,index) in form" :key='index'>
				<div>{{item.name}}</div>
				<el-input disabled v-model="item.value" style="width: 35%;margin-top: 2%;" size="mini"></el-input>
			</div>
		</div>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				backgroundDiv: {
				backgroundImage: "url(" + require("../../assets/img/cp.png") + ")",
				backgroundRepeat:'no-repeat',
				 backgroundPosition: '28%',

				 },
				msg:'',
				form:[
					{
						name:'湿度(%RH)',
						value:'30'
					},
					{
						name:'料位计(袋)',
						value:'30'
					},
					{
						name:'压差(Pa)',
						value:'30'
					},
					{
						name:'风量(m3/h)',
						value:'30'
					},
					{
						name:'温度(℃)',
						value:'30'
					},
					{
						name:'压力(Pa)',
						value:'30'
					},
					{
						name:'粉尘密度(mg/m3)',
						value:'30'
					},
					{
						name:'电流',
						value:'An'
					}
				]
			}
		},
		created: function() {
			this.msg = this.$route.query.key
		},
	}
</script>

<style scoped="scoped">
	.label{
		width: 6.875rem;
		text-align: center;
		background-color: #E8F4FF;
	}
	.msg_con{
		width: 60%;
		margin-left: 15%;
    font-size: 1.0rem;
	}
	.cp_msg{
		width: 70%;
		margin-left: 15%;
		margin-top: 1.5%;
		display: flex;
		justify-content: space-between;
		flex-wrap: wrap;
		height: 28.125rem;
     font-size: 1.0rem;
	}
	@media screen and (max-width: 1024px) {
		.msg_con{
			width: 100%;
			margin-left: 0;
      font-size: 0.9rem;
		}
		.cp_msg{
			width: 120%;
			margin-left: 0;
      font-size: 0.9rem;
		}
	}
</style>
