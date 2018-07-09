<template>
    <div class="envment">
        <el-form ref="form" :model="form" label-width="80px">
            <el-form-item label="PHP">
                <el-input v-model="form.name" readonly="readonly" value="PHP"></el-input>
            </el-form-item>
            <el-form-item label="环境">
                <el-col :span="11">
                <el-select v-model="form.region" placeholder="请选择要创建的环境">
                    <el-option label="dev" value="dev"></el-option>
                    <el-option label="beta" value="beta"></el-option>
                    <el-option label="gray" value="gray"></el-option>
                    <el-option label="pt" value="pt"></el-option>
                </el-select>
                </el-col>
            </el-form-item>
            <el-form-item label="环境">
                <el-col :span="11">
                    <el-input v-model="form.branch" placeholder="分支名称"></el-input>
                </el-col>
            </el-form-item>

            <el-form-item>
                <el-button type="primary" @click="onSubmit" >立即创建</el-button>
                <!--<el-button type="primary" @click="onSubmit" :loading="addLoading">立即创建</el-button>-->
                <el-button>取消</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
    export default {
        data() {
            name:'envment'
            return {
                form: {
                    name: '',
                    region: '',
                    branch:'',
                    addLoading: false
                },
            }
        },
        methods: {
            onSubmit(e) {
                // this.$refs.from.validate((valid) => {
                //     if (valid) {
                //         console.log(valid);
                //         this.addLoading = true;
                //         var envparms = {
                //             // env:this.form.region,
                //             branch:this.from.branch
                //         }
                //         var obj=JSON.stringify(envparms);
                //         console.log(envparms)
                //     }
                // });
                this.addLoading = true;
                // var envparms = {
                //     // env:this.form.region,
                //     branch:this.from.branch
                // }
                var envparms = this.from.name;
                var obj=JSON.stringify(envparms);
                console.log(envparms)
                e.preventDefault(e);
            }
        }
    }
</script>

<style>
    .envment{
        background: #fff;
        width: 55%;
        height: 100%;
        padding: 30px;
        box-shadow: 2px 0px 10px #ccc;
        margin: 0 auto;
    }
    .el-form-item{
        margin-bottom: 20px;
    }
</style>
