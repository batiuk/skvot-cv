<script>
import JsonBox from '../json-box.vue';

export default {
  name: 'JsonObject',
  props: {
    jsonValue: {
      type: Object,
      required: true,
    },
    keyName: {
      type: String,
      default: '',
    },
    links: {
      type: Object,
    },
    depth: {
      type: Number,
      default: 0,
    },
    expand: Boolean,
    sort: Boolean,
  },
  computed: {
    ordered() {
      if (!this.sort) {
        return this.jsonValue;
      }
      const ordered = {};
      Object.keys(this.jsonValue).sort().forEach((key) => {
        ordered[key] = this.jsonValue[key];
      });
      return ordered;
    },
  },
  methods: {
    toggle() {
      this.$emit('update:expand', !this.expand);
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
    if (!this.keyName) {
      let href = '#';
      try {
        href = this.links[this.keyName] ? `#${this.links[this.keyName]}` : '#';
        // eslint-disable-next-line no-empty
      } catch (e) {
      }
      elements.push(h('a', {
        class: {
          'jv-toggle': true,
          open: !!this.expand,
        },
        on: {
          click: this.toggle,
        },
        domProps: {
          href,
        },
      }));
    }
    elements.push(h('span', {
      class: {
        'jv-item': true,
        'jv-object': true,
      },
      domProps: {
        innerHTML: '{',
      },
    }));
    // eslint-disable-next-line no-restricted-syntax
    for (const key in this.ordered) {
      // eslint-disable-next-line no-prototype-builtins
      if (this.ordered.hasOwnProperty(key)) {
        const value = this.ordered[key];
        elements.push(h(JsonBox, {
          key,
          style: {
            display: !this.expand ? 'none' : undefined,
          },
          props: {
            sort: this.sort,
            keyName: key,
            depth: this.depth + 1,
            links: this.links,
            value,
          },
        }));
      }
    }
    if (!this.expand) {
      let href = '#';
      try {
        href = this.links[this.keyName] ? `#${this.links[this.keyName]}` : '#';
        // eslint-disable-next-line no-empty
      } catch (e) {
      }
      elements.push(h('a', {
        style: {
          display: this.expand ? 'none' : undefined,
        },
        class: {
          'jv-ellipsis': true,
        },
        on: {
          click: this.toggle,
        },
        attrs: {
          title: `click to reveal object content (keys: ${Object.keys(this.ordered).join(', ')})`,
        },
        domProps: {
          innerHTML: '...',
          href,
        },
      }));
    }
    elements.push(h('span', {
      class: {
        'jv-item': true,
        'jv-object': true,
      },
      domProps: {
        innerHTML: '}',
      },
    }));
    return h('span', elements);
  },
};
</script>
