<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <medium-editor
          :text="text"
          :options="options"
          v-on:edit="processEditOperation"
          custom-tag="textarea"
        ></medium-editor>
      </div>
    </div>
  </div>
</template>

<script>
import editor from "vue2-medium-editor";

export default {
  name: "app",
  components: {
    "medium-editor": editor
  },
  data: () => ({
    text: "",
    options: {
      activeButtonClass: "medium-editor-button-active",
      buttonLabels: false,
      contentWindow: window,
      delay: 0,
      disableReturn: false,
      disableDoubleReturn: false,
      disableExtraSpaces: false,
      disableEditing: false,
      elementsContainer: false,
      extensions: {},
      ownerDocument: document,
      spellcheck: true,
      targetBlank: false,
      toolbar: {
        /* These are the default options for the toolbar,
           if nothing is passed this is what is used */
        buttons: [
          "bold",
          "italic",
          "underline",
          "anchor",
          "h2",
          "h3",
          "justifyLeft",
          "justifyCenter",
          "justifyRight",
          "justifyFull"
        ],
        static: false,

        /* options which only apply when static is true */
        align: "center",
        sticky: false,
        updateOnEmptySelection: false
      }
    }
  }),
  methods: {
    processEditOperation: function(operation) {
      this.text = operation.api.origElements.innerHTML;
    }
  }
};
</script>

<style>
@import "./assets/css/bootstrap.css";
</style>
