<template>
  <div>
    <div class="node"
         @click="nodeClicked"
         :style="{'margin-left': `${depth * 20}px`}">
      <span
          class="type"
          v-if="hasChildren"
      >
        {{ expanded && node.type != 'link' ? '&#9660;' : '&#9658;' }}
      </span>
      <span class="type" v-else>&#9671;</span>
      <span
          :style="getStyle(node)">{{ node.name }}</span>
    </div>

    <span v-if="expanded">
    <TreeBrowser
        v-for="child in node.contents"
        :key="child.name"
        :node="child"
        :depth="depth + 1">
    </TreeBrowser>
      </span>
  </div>
</template>

<script>
// import ColorHash from 'color-hash';

// const colorHash = new ColorHash();

export default {
  name: "TreeBrowser",
  props: {
    node: Object,
    depth: {
      type: Number,
      default: 0,
    }
  },
  data() {
    return {
      expanded: false,
    }
  },
  methods: {
    nodeClicked() {
      this.expanded = !this.expanded
      if (!this.hasChildren) {
        alert(this.node.name)
      }
    },
    getStyle(node) {
      let colorDir = 'red'
      let colorLink = 'pink'
      if (node.type === 'file') {
        return {
          color: "green",
          // 'color': colorHash.hex(node.name.split('.')[1]),
        }
      } else if (node.type === 'link') {
        return {
          color: colorLink
        }
      } else return {
        color: colorDir
      }
    }
  },
  computed: {
    hasChildren() {
      return this.node.contents;
    }
  }
}

</script>

<style scoped>
.type {
  margin-right: 20px;
}

.node {
  text-align: left;
  font-size: 18px;
}
</style>