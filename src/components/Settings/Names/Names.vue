<!--suppress HtmlFormInputWithoutLabel -->
<template>
  <v-content>
    <Select
      label="settings.name-style"
      v-bind:current-item-id="settings.nameStyleId"
      v-bind:items="validValues.nameStyles"
      @change="settings.nameStyleId = $event"
    />
    <Checkbox
      label="settings.style-limit-break"
      v-bind:initialCheckboxValue="settings.styleLimitBreak"
      @change="settings.styleLimitBreak = $event"
    />
    <Checkbox
      label="settings.blur-names"
      v-bind:initialCheckboxValue="settings.blurNames"
      @change="settings.blurNames = $event"
    />
    <ColorPicker
      label="settings.percent-bar-font-color"
      v-bind:initial-color="settings.percentBarFontColor"
      @change="settings.percentBarFontColor = $event"
    />
    <SettingButtons @reset="reset" @update="update" />
  </v-content>
</template>

<script>
import ColorPicker from "../../Common/ColorPicker";
import SettingButtons from "../../Common/SettingButtons";
import Checkbox from "../../Common/Checkbox";
import Select from "../../Common/Select";

export default {
  name: "Names",
  components: { ColorPicker, Checkbox, Select, SettingButtons },
  data() {
    return {
      settings: {
        nameStyleId: this.$store.state.settings.nameStyleId,
        styleLimitBreak: this.$store.state.settings.styleLimitBreak,
        blurNames: this.$store.state.settings.blurNames,
        percentBarFontColor: this.$store.state.settings.percentBarFontColor
      },
      validValues: {
        nameStyles: this.$store.state.validValues.nameStyles
      }
    };
  },
  methods: {
    reset() {
      this.$emit("reset", this.settings);
    },
    update() {
      this.$emit("update", this.settings);
    }
  }
};
</script>
