vue router 知识点

router 传参
1.配置路径
    export default new Router({
    routes: [
        {
        path: '/testVueRouter',
        name: 'TestVueRouter',
        component: TestVueRouter
        },
        {
        path: '/testVueRouterTo',
        // 一定要写name,params必须用name来识别路径
        name: 'TestVueRouterTo',
        component: TestVueRouterTo
        }
    ]
    })
2.参数设置
    <!-- test-vue-router页面 -->
    <template>
    <div>
        <a @click="routerTo()">query传参</a>
    </div>
    </template>
    <script>
    export default {
    methods: {
        routerTo() {
        this.$router.push({
            name: `TestVueRouterTo`,
            <!-- 注意！ 这里的参数传递，params是一次性的，页面刷新参数就清空了；-->
            params: {
                page: '1', code: '8989'
            }
            <!-- 而query是可以随页面刷新一直存在的 -->
            query: {
                page: '1', code: '8989'
            }
        })
        }
    }
    }
    </script>
3.接受参数
    <!-- test-vue-router-to页面 -->
    <template>
    <div>
    </div>
    </template>
    <script>
    export default{
    data() {
        return {
            page: '',
            code: ''
        }
    },
    created() {
        this.getRouterData()
    },
    methods: {
        getRouterData() {
        this.page = this.$route.params.page
        this.code = this.$route.params.code
        console.log('page', this.page)
        console.log('code', this.code)
        }

    }
    }
    </script>