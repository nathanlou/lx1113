<template>
	<div class="overview_container">
		<el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" label-position='right' class="demo-ruleForm">
			<div style="display: flex;justify-content: space-between;">
				<el-form-item label="企业" prop="company" size="mini" style="color: gray;">
					<el-select v-model="ruleForm.company" placeholder="请选择" >
						<el-option label="潜合测试" value="qianhe"></el-option>
						<el-option label="客户体验" value="kehu"></el-option>
					</el-select>
				</el-form-item>
				<el-form-item label="设备编号" prop="bh" style='width: 45%;'>
					<el-input v-model="ruleForm.bh"></el-input>
				</el-form-item>
			</div>
			<div style="display: flex;justify-content: space-between;">
				<el-form-item label="内部编号" prop="nbbh" style='width: 45%;'>
					<el-input v-model="ruleForm.nbbh"></el-input>
				</el-form-item>
				<el-form-item label="SIM卡号" prop="sim" style='width: 45%;'>
					<el-input v-model="ruleForm.sim"></el-input>
				</el-form-item>
			</div>
			<div style="display: flex;justify-content: space-between;">
				<el-form-item label="设备种类" prop="sbzl" style='width: 45%;'>
					<el-select v-model="ruleForm.sbzl" placeholder="请选择">
						<el-option label="YLY1" value="yly1"></el-option>
						<el-option label="云智能控制仪" value="yun"></el-option>
					</el-select>
				</el-form-item>
				<el-form-item label="设备型号" prop="sbxh" style='width: 45%;'>
					<el-select v-model="ruleForm.sbxh" placeholder="请选择">
						<el-option label="1型" value="1"></el-option>
						<el-option label="2型" value="2"></el-option>
					</el-select>
				</el-form-item>
			</div>
			<div style="display: flex;justify-content: space-between;">
				<el-form-item label="工地负责人" prop="gdfzr" style='width: 45%;'>
					<el-input v-model="ruleForm.gdfzr"></el-input>
				</el-form-item>
				<el-form-item label="手机号码" prop="phone" style='width: 45%;'>
					<el-input v-model="ruleForm.phone"></el-input>
				</el-form-item>
			</div>
			<div style="display: flex;justify-content: space-between;">
				<el-form-item label="安装日期" required style='width: 45%;'>
						<el-form-item prop="azrq">
							<el-date-picker type="date" placeholder="选择日期" v-model="ruleForm.azrq" style="width: 100%;"></el-date-picker>
						</el-form-item>
				</el-form-item>
				<el-form-item label="缴费日期" required style='width: 45%;'>
						<el-form-item prop="jfrq">
							<el-date-picker type="date" placeholder="选择日期" v-model="ruleForm.jfrq" style="width: 100%;"></el-date-picker>
						</el-form-item>
				</el-form-item>
			</div>
			<div style="display: flex;justify-content: space-between;">
				<el-form-item label="当前地址" prop="dqdz" style='width: 45%;'>
					<el-input v-model="ruleForm.dqdz"></el-input>
				</el-form-item>
				<el-form-item label="生产厂家" prop="sccj" style='width: 45%;'>
					<el-input v-model="ruleForm.sccj"></el-input>
				</el-form-item>
			</div>
			<div style="display: flex;justify-content: space-between;">
				<el-form-item label="工地名称" prop="gdmc" style='width: 45%;'>
					<el-input v-model="ruleForm.gdmc"></el-input>
				</el-form-item>
				<el-form-item label="备注" prop="bz" style='width: 45%;'>
					<el-input></el-input>
				</el-form-item>
			</div>
			<el-form-item>
				<el-button type="primary" @click="submitForm('ruleForm')">确认修改</el-button>
			</el-form-item>
		</el-form>
	</div>
</template>

<script>
	export default {
		data() {
			var cart = (rule, value, callback) => {
        if (!value) {
          return callback(new Error('sim卡号不能为空'));
        }
        setTimeout(() => {
          if (Number.isInteger(value)) {
            callback(new Error('请输入数字值'));
          } else {
             if (value.length != 13) {
              callback(new Error('必须13位'));
            } else {
              callback();
            }
          }
        }, 1000);
      };
			// 此处自定义校验手机号码js逻辑
    var phoneReg = /^[1][3,4,5,7,8][0-9]{9}$/
    var validatePhone = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('号码不能为空!!'))
      }
      setTimeout(() => {
        if (!phoneReg.test(value)) {
          callback(new Error('格式有误'))
        } else {
          callback()
        }
      }, 1000)
    }
			return {
				ruleForm: {
					company: '',
					bh: '',
					nbbh:'',
					sim:'',
					sbzl:'',
					sbxh:'',
					gdfzr:'',
					phone:'',
					azrq: '',
					jfrq: '',
					dqdz:'',
					sccj:'',
					gdmc:'',
					bz:'',
				},
				rules: {
					bh: [
						{
							required: true,
							message: '该项为必填项',
							trigger: 'blur'
						}
					],
					nbbh: [
						{
							required: true,
							message: '该项为必填项',
							trigger: 'blur'
						}
					],
					gdfzr: [
						{
							required: true,
							message: '该项为必填项',
							trigger: 'blur'
						}
					],
					phone: [
						{
							required: true,
							trigger: 'blur',
							validator: validatePhone,
						}
					],
					sim: [
						{
							required: true,
							trigger: 'blur',
							validator:cart
						}
					],
					company: [{
						required: true,
						message: '该项为必填项',
						trigger: 'change'
					}],
					sbzl: [{
						required: true,
						message: '该项为必填项',
						trigger: 'change'
					}],
					sbxh: [{
						required: true,
						message: '该项为必填项',
						trigger: 'change'
					}],
					azrq: [{
						type: 'date',
						required: true,
						message: '请选择日期',
						trigger: 'change'
					}],
					jfrq: [{
						type: 'date',
						required: true,
						message: '请选择时间',
						trigger: 'change'
					}],

				}
			};
		},
		created: function() {
			this.ruleForm = this.$route.query.key
			console.log(this.$route.query.key)
		},
		methods: {
			submitForm(formName) {
				this.$refs[formName].validate((valid) => {
					if (valid) {
						alert('submit!');
					} else {
						console.log('error submit!!');
						return false;
					}
				});
			},
			resetForm(formName) {
				this.$refs[formName].resetFields();
			}
		}
	}
</script>

<style>
	.overview_container {
		width: 95%;
		margin-left: 2%;
    color: gray;
    margin-top: 1%;
	}
</style>
