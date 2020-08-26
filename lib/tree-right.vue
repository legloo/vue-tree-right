<template>
  <div class="TreeRight" v-if="list.length">
    <div class="childs">
      <div class="child" v-for="(item,index) in list" :key="item.id +'-child-'+index">
        <div
          class="child-item"
          :style="{marginRight: item.children && item.children.length > 1 ? '20px' :''}"
        >
          <div class="childname" :id="item.id">
            <div class="shows">
              <p
                v-for="(itemshow,index3) in showfields"
                :key="'itemshow'+index3"
              >{{itemshow.name}}{{item[itemshow.key]}}</p>
            </div>
            <div class="position-arrow" v-if="list.length > 1">
              <img src="@/assets/arrow-right.png" width="20" alt />
            </div>
            <div
              class="position-top"
              v-if="isFirst(item.id) && domready"
              :style="position_top(item.id,'top')"
            ></div>
            <div
              class="position-top"
              v-if="isLast(item.id)"
              :style="position_top(item.id,'bottom')"
            ></div>
          </div>
          <div
            class="childarrow"
            :style="{borderRight:item.children && item.children.length >1 ? '1px solid #000' : '3px solid transparent'}"
          >
            <img src="@/assets/arrow-right.png" width="20" alt />
          </div>
        </div>
        <div class="child-children" v-if="item.children && item.children.length">
          <TreeRight :list="item.children" :showfields="showfields" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TreeRight",
  components: {},
  data() {
    return {
      domready: false,
    };
  },
  props: {
    list: {
      type: Array,
      default: () => [],
    },
    showfields: {
      type: Array,
      default: () => [],
    },
  },

  mounted() {
    this.$nextTick(() => {
      this.domready = true;
    });
  },
  methods: {
    position_top(id, position) {
      let dom = document.getElementById(id);
      let height;
      if (dom) {
        height = dom.clientHeight;
      }
      let rt;
      if (position === "top") {
        rt = {
          height: height / 2 - 2 + "px",
          top: 0,
        };
      }
      if (position === "bottom") {
        rt = {
          height: height / 2 + 1 + "px",
          bottom: 0,
        };
      }
      return rt;
    },

    isFirst(id) {
      return (
        this.list.length > 1 && this.list.map((x) => x.id).indexOf(id) === 0
      );
    },

    isLast(id) {
      return (
        this.list.length > 1 &&
        this.list.map((x) => x.id).indexOf(id) === this.list.length - 1
      );
    },
  },
};
</script>

<style lang="less" scoped>
.TreeRight {
  p {
    margin: 0;
    font-size: 13px;
  }
  display: flex;
  .father {
    width: 70px;
    background-color: red;
    padding: 100px 10px;
  }
  .childs {
    .child {
      display: flex;
      background-color: #fff;
      .child-item {
        display: flex;
        align-items: center;
        margin: 10px 0;
        .childname {
          .shows {
            text-align: left;
            border: 1px solid #000;
            padding: 10px;
            height: 100px;
            border-radius: 5px;
            width: 100%;
            // color: #fff;
          }
          // box-sizing: content-box;
          cursor: pointer;
          height: 100%;
          display: flex;
          align-items: center;
          // border: 1px solid #000;
          width: 120px;
          text-align: center;
          justify-content: center;
          position: relative;
          padding: 10px 0;
          .position-arrow {
            position: absolute;
            // top: 50%;
            left: -22px;
          }
          .position-top {
            position: absolute;
            width: 3px;
            background-color: #fff;
            left: -23px;
            height: 10px;
          }
        }
        .childarrow {
          height: 100%;
          // border-right: ;
          display: flex;
          align-items: center;
        }
      }
    }
    .child-children {
      display: flex;
      flex-direction: column;
      justify-content: center;
    }
  }
}
</style>
