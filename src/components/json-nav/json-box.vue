<script>
import JsonString from './types/json-string.vue';
import JsonUndefined from './types/json-undefined.vue';
import JsonNumber from './types/json-number.vue';
import JsonBoolean from './types/json-boolean.vue';
import JsonObject from './types/json-object.vue';
import JsonArray from './types/json-array.vue';
import JsonFunction from './types/json-function.vue';

export default {
  name: 'JsonBox',
  inject: ['expandDepth'],
  props: {
    value: {
      type: [Object, Array, String, Number, Boolean, Function],
      default: null,
    },
    keyName: {
      type: String,
      default: '',
    },
    sort: Boolean,
    depth: {
      type: Number,
      default: 0,
    },
    links: {
      type: Object,
    },
  },
  data() {
    return {
      expand: true,
    };
  },
  mounted() {
    this.expand = !(this.depth >= this.expandDepth);
  },
  methods: {
    toggle() {
      this.expand = !this.expand;
      try {
        this.$el.dispatchEvent(new Event('resized'));
      } catch (e) {
        // handle IE not supporting Event constructor
        const evt = document.createEvent('Event');
        evt.initEvent('resized', true, false);
        this.$el.dispatchEvent(evt);
      }
    },
  },
  render(h) {
    const elements = [];
    let dataType;
    if (this.value === null || this.value === undefined) {
      dataType = JsonUndefined;
    } else if (Array.isArray(this.value)) {
      dataType = JsonArray;
    } else if (typeof this.value === 'object') {
      dataType = JsonObject;
    } else if (typeof this.value === 'number') {
      dataType = JsonNumber;
    } else if (typeof this.value === 'string') {
      dataType = JsonString;
    } else if (typeof this.value === 'boolean') {
      dataType = JsonBoolean;
    } else if (typeof this.value === 'function') {
      dataType = JsonFunction;
    }
    if (this.keyName
          && (this.value && (Array.isArray(this.value) || typeof this.value === 'object'))) {
      elements.push(h('span', {
        class: {
          'jv-toggle': true,
          open: !!this.expand,
        },
        on: {
          click: this.toggle,
        },
      }));
    }
    if (this.keyName) {
      let href = '#';
      try {
        href = this.links[this.keyName] ? `#${this.links[this.keyName]}` : '#';
        // eslint-disable-next-line no-empty
      } catch (e) {
      }

      elements.push(h('a', {
        class: {
          'jv-key': true,
        },
        on: {
          click: this.toggle,
        },
        domProps: {
          innerHTML: `${this.keyName}:`,
          href,
        },
      }));
    }
    elements.push(h(dataType, {
      class: {
        'jv-push': true,
      },
      props: {
        jsonValue: this.value,
        keyName: this.keyName,
        sort: this.sort,
        links: this.links,
        depth: this.depth,
        expand: this.expand,
      },
      on: {
        'update:expand': (value) => {
          this.expand = value;
        },
      },
    }));
    return h('div', {
      class: {
        'jv-node': true,
      },
    }, elements);
  },
};
</script>

<style lang="scss">
  .jv-node {
    position: relative;

    &:after {
      content: ','
    }

    &:last-of-type {
      &:after {
        content: ''
      }
    }

    & .jv-node {
      margin-left: 25px;
    }
  }
</style>
