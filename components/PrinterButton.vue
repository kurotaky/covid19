<template>
  <div :class="wrapperClass">
    <v-btn
      class="PrinterButton"
      outlined
      href="/print/flow"
      target="_blank"
      @mouseover="mouseover"
      @mouseleave="mouseleave"
    >
      <div class="PrinterButton-PrinterIcon">
        <PrinterWhiteIcon v-if="hover" aria-hidden="true" />
        <PrinterIcon v-else aria-hidden="true" />
      </div>
      <span class="PrinterButton-Text">
        {{ $t('print') }}
      </span>
    </v-btn>
  </div>
</template>

<i18n src="./PrinterButton.i18n.json"></i18n>

<script>
import PrinterIcon from '@/static/printer.svg'
import PrinterWhiteIcon from '@/static/printer-white.svg'

export default {
  components: {
    PrinterIcon,
    PrinterWhiteIcon
  },
  props: {
    wrapperClass: {
      type: String,
      required: false,
      default: ''
    }
  },
  data() {
    return {
      hover: this.hover
    }
  },
  methods: {
    mouseover() {
      this.hover = true
    },
    mouseleave() {
      this.hover = false
    }
  }
}
</script>

<style lang="scss" scoped>
.PrinterButton {
  @include button-text('md');
  &:hover {
    color: $white !important;
  }
  &-Text {
    margin: 6px auto 0;
    @include lessThan($small) {
      position: absolute !important;
      height: 1px !important;
      width: 1px !important;
      padding: 0 !important;
      border: 0 !important;
      white-space: nowrap !important;
      overflow: hidden !important;
      clip: rect(1px, 1px, 1px, 1px) !important;
      clip-path: inset(50%) !important;
    }
  }
  &-PrinterIcon {
    margin-top: 8px;
    width: 25px;

    @include largerThan($small) {
      padding-right: 7px;
    }
    svg {
      width: auto;
    }
  }
}
</style>
