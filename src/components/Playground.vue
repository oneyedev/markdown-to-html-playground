<template>
  <div class="wrapper">
    <div class="flex">
      <h3 class="header">
        Markdown (Input)
        <select v-model="inputText" @change="onChangeInputText(inputText)">
          <option value="custom">Custom</option>
          <option value="sample">Sample</option>
        </select>
      </h3>
      <textarea v-model="markdown" placeholder="Insert your Markdown Text"></textarea>
    </div>
    <div class="flex">
      <h3 class="header">
        HTML (Output)
        <select v-model="outputStyle">
          <option value>Only HTML</option>
          <option value="markdown-body">github-markdown-css</option>
        </select>
      </h3>
      <div class="output">
        <vue-showdown :markdown="markdown" flavor="github" :class="outputStyle"></vue-showdown>
      </div>
    </div>
  </div>
</template>

<script>
const SAMPLE_MARKDOWN = `# This is a h1
## This is a h2 
### This is a h3
#### This is a h4
##### This is a h5
###### this is a h6
***
- This is a unordered item1
- This is a unordered item2
- This is a unordered item3

1. This is a ordered item1
1. This is a ordered item2
1. This is a ordered item3

* depth1
 * depth2
   * depth3 is not working! (maybe.. bug?)

***
[This is a hyper link](https://google.com)
![This is a image](https://picsum.photos/200/200/?random)
![This is a image alt](https://)
***

<center>This text is centered</center>
**This is a emphasizing text**
*This is a italic-style text*

\`\`\`
This is a code block
\`\`\`
\`\`\`js
const HELLO_WORLD = 'Hello World!'
\`\`\`
> This is a block quote
`;
export default {
  data() {
    return {
      markdown: SAMPLE_MARKDOWN,
      inputText: "sample",
      outputStyle: "markdown-body"
    };
  },
  methods: {
    onChangeInputText(value) {
      if (value === "sample") {
        this.markdown = SAMPLE_MARKDOWN;
      } else {
        this.markdown = "";
      }
    }
  }
};
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-wrap: wrap;
}
textarea {
  font-size: 15px;
  width: 95%;
  min-height: 600px;
  padding: 5px;
  border: black solid 1px;
  resize: vertical;
}
@media screen and (max-width: 600px) {
  .flex {
    width: 100%;
  }
}
@media screen and (min-width: 601px) {
  .flex {
    width: 50%;
  }
}
.header {
  text-align: center;
}
.output {
  border: black solid 1px;
  min-height: 600px;
  padding: 5px;
}
</style>
