<script>
export default {
  name: 'JsonNumber',
  functional: true,
  props: {
    jsonValue: {
      type: Number,
      required: true,
    },
  },
  render(h, { props }) {
    return h('span', {
      class: {
        'jv-item': true,
        'jv-number': true,
      },
      domProps: {
        innerHTML: props.jsonValue.toString(),
      },
    });
  },
};
</script>
