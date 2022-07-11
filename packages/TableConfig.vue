<template>
  <div class="widget-config">
    <el-form
      label-suffix="："
      v-if="this.data && Object.keys(this.data).length > 0"
      labelPosition="left"
      labelWidth="90px"
      size="small"
    >
      <el-collapse v-model="collapse">
        <el-collapse-item name="1" title="基本属性">
          <el-form-item label="列宽度">
            <el-input-number
              style="width: 100%"
              v-model="data.width"
              controls-position="right"
              placeholder="宽度"
              :min="100"
            ></el-input-number>
          </el-form-item>
          <el-form-item
            label="标题宽度"
            v-if="!['group', 'dynamic', 'title'].includes(data.type)"
          >
            <el-input-number
              v-model="data.labelWidth"
              :min="80"
              :step="10"
              controls-position="right"
              placeholder="标签宽度"
              style="width: 100%"
            ></el-input-number>
          </el-form-item>
          <el-form-item label="是否隐藏">
            <el-switch v-model="data.hide"></el-switch>
          </el-form-item>
          <el-form-item label="是否搜索">
            <el-switch v-model="data.search"></el-switch>
          </el-form-item>
          <el-form-item label="超宽隐藏">
            <el-switch v-model="data.overHidden"></el-switch>
          </el-form-item>
        </el-collapse-item>
      </el-collapse>
    </el-form>
    <template v-else>
      <avue-empty
        v-if="avueVersion('2.9.4')"
        desc="拖拽字段进行配置"
        style="margin-top: 100%"
      ></avue-empty>
      <el-empty
        v-else
        description="拖拽字段进行配置"
        style="margin-top: 100%"
      ></el-empty>
    </template>
  </div>
</template>

<script>
import fields from "./fieldsConfig.js";

export default {
  name: "table-config",
  props: ["data", "defaultValues"],
  data() {
    return {
      fields,
      collapse: ["1"],
      validator: {
        type: null,
        required: null,
        pattern: null,
        length: null,
      },
    };
  },
  methods: {},
};
</script>
