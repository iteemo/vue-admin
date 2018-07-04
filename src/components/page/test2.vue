<template>
    <el-table
        :data="data"
        border
        style="width: 100%">
        <el-table-column
            prop="create_time"
            label="创建时间"
            width="180">
        </el-table-column>
        <el-table-column
            prop="repository"
            label="所在仓库"
            width="180">
        </el-table-column>
        <el-table-column
            prop="size"
            label="镜像大小"
            width="180">
        </el-table-column>
        <el-table-column
            prop="tag"
            label="版本">
        </el-table-column>
    </el-table>
</template>
<!--<template>-->
    <!--<div class="table" >-->
        <!--<div class="row" v-for="item in list1">-->
            <!--<span>{{item.create_time}}  </span>-->
            <!--<span>{{item.repository}}</span>-->
            <!--<span>{{item.size}}</span>-->
            <!--<span>{{item.tag}}</span>-->
        <!--</div>-->
    <!--</div>-->
<!--</template>-->

<script>
    export default {
        name: 'test2',
        data() {
            return {
                list1: [

                ],
                url: '/dvd-docker/v1.0/image/images',
                tableData: [],
                cur_page: 1,
                multipleSelection: [],
                select_cate: '',
                select_word: '',
                del_list: [],
                is_search: false,
                editVisible: false,
                delVisible: false,
                form: {
                    name: '',
                    date: '',
                    address: ''
                },
                idx: -1
            }
        },
        created() {
            this.getData();
        },
        computed: {
            data() {

            }
        },
        methods: {
            getData() {
                this.$axios.get('/api/dvd-docker/v1.0/image/images?repository=centos&tag=6.6', {
                    page: this.cur_page
                }).then((res) => {
                    this.list1 = res.data;
                    this.list1.splice("create_time","repository","tag")
                })

            }
        }
    }

</script>
