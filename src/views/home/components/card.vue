<template>
  <div class="card">
    <el-row class="h100 panel-group" :gutter="12">
      <el-col :span="6" v-for="item in panel_group_list" :key="item.id">
        <el-card class="h100 box-card col-between" shadow="hover" :body-style="{ padding: '0 20px' }">
          <template #header>
            <div class="card-header row-between">
              <span>{{ item.label }}</span>
              <el-tag type="success">{{ item.date }}</el-tag>
            </div>
          </template>
          <div class="col-between h100">
            <div>
              <span class="fs35">{{ item.number }}</span>
              <br />
              <div class="mt10">
                <span class="pr20">
                  <span>日同比 {{ item.day_compare }}%</span>
                  <el-icon class="icon"><caret-top /></el-icon>
                </span>
                <span>
                  <span>周同比 {{ item.week_compare }}%</span>
                  <el-icon class="icon"><caret-top /></el-icon>
                </span>
              </div>
              <el-divider class="divider-style"></el-divider>
            </div>
            <div class="row-between pt10 pb15">
              <span>{{ item.total_title }}</span>
              <span>{{ item.total_number }}</span>
            </div>
          </div>
        </el-card>
      </el-col>
    </el-row>
    <el-row class="h100 menu-group mt10" :gutter="12">
      <el-col :span="3" v-for="item in menu_group_list" :key="item.id">
        <el-card class="h100 box-card" shadow="hover" :body-style="{ padding: '0 20px' }">
          <div class="col-between row-center">
            <el-icon class="icon fs28 w100 m10 pt10"> <component :is="item.icon" /> </el-icon>
            <div class="mb10">{{ item.label }}</div>
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script lang="ts">
import { defineComponent, onBeforeMount, reactive, toRefs } from 'vue';
import { CaretTop } from '@element-plus/icons-vue';
import { UserFilled, Setting, GoodsFilled, Management, Comment, Flag, TrendCharts, Ticket } from '@element-plus/icons-vue';

export default defineComponent({
  name: '',
  components: { CaretTop, UserFilled, Setting, GoodsFilled, Management, Comment, Flag, TrendCharts, Ticket },
  setup() {
    const panel_group_list = [
      { id: 1, label: '销售额', date: '昨日', number: '9', day_compare: '10', week_compare: '33', total_title: '总销售额', total_number: '288元' },
      { id: 2, label: '用户访问量', date: '昨日', number: '3233', day_compare: '545', week_compare: '889', total_title: '总访问量', total_number: '4583次' },
      { id: 3, label: '订单量', date: '昨日', number: '7282', day_compare: '22', week_compare: '465', total_title: '总订单量', total_number: '5739单' },
      { id: 4, label: '新增用户', date: '昨日', number: '33', day_compare: '8', week_compare: '372', total_title: '总用户', total_number: '3929人' }
    ];
    const menu_group_list = [
      { id: 1, label: '用户管理', icon: 'UserFilled', url: '/' },
      { id: 2, label: '系统设置', icon: 'Setting', url: '/' },
      { id: 3, label: '商品', icon: 'GoodsFilled', url: '/' },
      { id: 4, label: '订单管理', icon: 'Management', url: '/' },
      { id: 5, label: '短信配置', icon: 'Comment', url: '/' },
      { id: 6, label: '注意事项', icon: 'Flag', url: '/' },
      { id: 7, label: '数据分析', icon: 'TrendCharts', url: '/' },
      { id: 8, label: '优惠券', icon: 'Ticket', url: '/' }
    ];
    const state = reactive({
      panel_group_list: panel_group_list,
      menu_group_list: menu_group_list
    });

    onBeforeMount(() => {});
    return { ...toRefs(state) };
  }
});
</script>
<style lang="scss" scpoed>
.card {
  .panel-group {
    height: 250px;
    .divider-style {
      margin: 25px 0 5px 0;
      .icon {
        color: red;
      }
    }
  }
  .menu-group {
    .icon {
      color: wheat;
    }
  }
  span {
    white-space: nowrap;
  }
}
</style>
