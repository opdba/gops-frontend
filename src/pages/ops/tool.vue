<template>
    <div>
        <div class="tool-page-right">
            <bread-bar :bread-items="breadItems"></bread-bar>
            <div class="tool-page-content">
                <Row v-for="(types,index) in toolList" :key="index">
                    <div class="tool-group-title">
                        <h3>{{types.type}}</h3>
                    </div>
                    <Col :xs="24" :sm="12" :md="6" :lg="4" class="tool-card"
                         v-for="(tool,index) in types.items" :key="index"
                         @click.native="goToSelected(tool.route)">
                    <Card>
                        <p>{{tool.name}}</p>
                    </Card>
                    </Col>
                </Row>
            </div>
        </div>
    </div>
</template>

<script>
    import BreadBar from '../../components/breadbar'

    export default {
        components: {
            BreadBar
        },
        data() {
            return {
                breadItems: ['运维作业'],
                toolList: [
                    {
                        "type": "本地",
                        "items": [
                            {
                                name: "租户备份",
                                route: "/ops/tool/01"
                            },
                            {
                                name: "租户迁移",
                                route: "/ops/tool/02"
                            },
//                            {
//                                name: "HTTP压力测试",
//                                route: "/ops/tool/03"
//                            },
                            {
                                name: "SSH免密码",
                                route: "/ops/tool/03"
                            }
                        ]
                    },
                    {
                        "type": "Ansible",
                        "items": [
                            {
                                name: "文件分发",
                                route: "/ops/tool/11"
                            },
                            {
                                name: "命令执行",
                                route: "/ops/tool/12"
                            },
                            {
                                name: "脚本执行",
                                route: "/ops/tool/13"
                            },
                            {
                                name: "Linux用户管理",
                                route: "/ops/tool/14"
                            }
                        ]
                    },
                    {
                        "type": "阿里云",
                        "items": [
                            {
                                name: "ECS启停",
                                route: "/ops/tool/21"
                            },
                            {
                                name: "ECS性能数据",
                                route: "/ops/tool/22"
                            },
                            {
                                name: "数据库管理",
                                route: "/ops/tool/23"
                            },
                            {
                                name: "RDS白名单",
                                route: "/ops/tool/24"
                            },
                            {
                                name: "RDS账号权限",
                                route: "/ops/tool/25"
                            },
                            {
                                name: "RDS资源使用数据",
                                route: "/ops/tool/26"
                            },
                            {
                                name: "RDS性能数据",
                                route: "/ops/tool/27"
                            },
                            {
                                name: "RDS会话",
                                route: "/ops/tool/28"
                            },
                            {
                                name: "SQL死锁",
                                route: "/ops/tool/29"
                            },
                            {
                                name: "SlowSQL",
                                route: "/ops/tool/30"
                            },


                        ]
                    },
                ]
            }
        },
        methods: {
            goToSelected(route) {
                this.$router.push(route)
            }
        }

    }
</script>

<style>
    .tool-page-right {
        position: fixed;
        left: 185px;
        top: 60px;
        right: 0;
        bottom: 0;
        overflow: scroll;
    }

    .tool-page-content {
        position: relative;
        min-height: 100%;
        top: 8px;
        margin-left: 8px;
        margin-right: 8px;
        margin-bottom: 8px;
        padding-top: 8px;
        padding-left: 8px;
        padding-right: 8px;
        padding-bottom: 36px;
        border-radius: 5px;
        background: white;
    }

    .tool-group-title {
        border-left: 2px solid gray;
        margin-left: 8px;
        padding-left: 8px;
        margin-top: 8px;
        background: linear-gradient(60deg, #f8f8f9, white);
    }

    .tool-card {
        padding: 8px;
        text-align: center;
    }
</style>
