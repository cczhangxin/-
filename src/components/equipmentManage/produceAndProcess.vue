<template>
    <div class="item-box">
        <!--面包屑-->
        <el-breadcrumb separator-class="el-icon-arrow-right">
            <el-breadcrumb-item>设备管理</el-breadcrumb-item>
            <el-breadcrumb-item>生产线和工序管理</el-breadcrumb-item>
        </el-breadcrumb>
        <!--搜索部分-->
        <header class="header-search">
            <el-input size="small" v-model="searchData.name" placeholder=" 请输入生产线名称" clearable
                      style="width: 220px;"></el-input>
            <el-button size="small" type="primary" icon="el-icon-search" @click="query()">查询</el-button>
            <el-button size="small" type="success" @click="newEquipment()" class="header-add-btn">新增生产线</el-button>
        </header>
        <!--内容-->
        <el-table :data="tableData" style="width: 100%" height="620" v-loading="loading" element-loading-text="拼命加载中">
            <el-table-column label="序号" type="index" width="50"></el-table-column>
            <el-table-column prop="name" label="生产线名称"></el-table-column>
            <el-table-column prop="number" label="生产线编号"></el-table-column>
            <el-table-column prop="number" label="工序信息"></el-table-column>
            <el-table-column label="操作" width="350">
                <template slot-scope="scope">
                    <el-button size="mini" type="success" @click="edit(scope.row)">修改</el-button>
                    <el-button size="mini" type="danger" @click="delete(scope.row)">删除</el-button>
                </template>
            </el-table-column>
        </el-table>
        <!--分页-->
        <el-pagination
                class="table-pagination"
                @size-change="handleSizeChange"
                @current-change="handleCurrentChange"
                :page-sizes="[10, 50, 100, 200]"
                :page-size=paginationData.pageSize
                layout="total, sizes, prev, pager, next, jumper"
                :total=paginationData.total>
        </el-pagination>
    </div>
</template>
<script>
    export default {
        data: function () {
            return {
                loading: false,
                searchData: {
                    name: '',
                },
                paginationData: {
                    pageNow: 1,
                    pageSize: 10,
                    total: 0
                },
            }
        },
        components: {},
        props: [],
        computed: {},
        created() {
        },
        mounted() {
        },
        methods: {
            handleSizeChange(val) {
                this.paginationData.pageSize = val
                this.getTableData()
            },
            handleCurrentChange(val) {
                this.paginationData.pageNow = val
                this.getTableData()
            },
            getData() {

            },
            query() {

            },
            edit() {

            },
            delete() {

            },
        },
        watch: {}
    }
</script>
<style scoped lang="less">
</style>
