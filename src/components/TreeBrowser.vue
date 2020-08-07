<template>
<div>
  <div class="node"
    :style="{ 'margin-left': `${depth * 20}px` }"
     @click="expanded = !expanded">
     <span class="type" v-if="hasChildren">
       {{ expanded ? '&#9660;' : '&#9658;' }}
     </span>
     {{ node.name }}
  </div>
   {{ hasChildren }}
  <div v-if="expanded">
      <TreeBrowser  v-for="child in node.children" :key="child.name" :node="child" :depth="depth + 1"/>
  </div>
</div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class TreeBrowser extends Vue {
  @Prop() private node!: any;
  @Prop({ default: 0}) private depth!: number;
  private expanded = false;

  public hasChildren() {
    return true
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.node {
  text-align: left;
  font-size: 18px;
}

</style>
