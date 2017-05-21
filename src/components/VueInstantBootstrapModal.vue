<template>
  <!-- container -->
  <transition name="modal" v-if="showModal">
    <div class="modal-mask"
         v-on:click="onModalMaskClicked()">
      <div class="modal-dialog" :class="[ 'modal-'+size ]">
        <div class="modal-content" v-on:click.stop="">
          <slot></slot>
        </div>
        <!-- /.modal-content -->
      </div>
      <!-- /.modal-dialog -->
    </div>
    <!-- /.modal -->
  </transition>
</template>
<script>
  export default {
    mounted () {
      if (this.closeOnEsc) {
        document.addEventListener("keydown", (e) => {
          if (this.show && e.keyCode == 27) {
            this.showModal = false;
          }
        });
      }
    },
    props: {
      size: {
        type: String,
        default: 'md'
      },
      closeOnBackdrop: {
        type: Boolean,
        default: true
      },
      closeOnEsc: {
        type: Boolean,
        default: true
      }
    },
    data () {
      var list = []
      return {
        notificationList: list,
        showModal: false
      }
    },
    methods: {
      onModalMaskClicked: function () {
        if (!this.closeOnBackdrop) {
          return;
        }
        this.showModal = false;
      },
      forceClose: function (notification) {
        notification.forceKilled = true
        this.sweep()
      },
      open: function () {
        this.showModal = true
      },
      show: function () {
        this.showModal = true
      },
      close: function () {
        this.showModal = false
      },
      hide: function () {
        this.showModal = false
      }
    },
    filters: {
      capitalize: function (str) {
        return str.charAt(0).toUpperCase() + str.slice(1)
      }
    }
  }
</script>
<style>
  .modal-mask {
    position: fixed;
    z-index: 9996;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, .2);
    display: block;
    -webkit-transition: opacity .3s ease-in-out;
    -o-transition: opacity .3s ease-in-out;
    transition: opacity .3s ease-in-out;
    overflow-y: auto!important;
  }

  .modal-content {
    border: 0px;
    border-radius: 2px;
    -webkit-transition: transform .3s ease-in-out;
    -o-transition: transform .3s ease-in-out;
    transition: transform .3s ease-in-out;
  }

  .modal-enter {
    opacity: 0;
  }

  .modal-leave-active {
    opacity: 0;
  }

  .modal-enter .modal-content {
    -webkit-transform: translate(0px, -20px);
    transform: translate(0px, -20px);
  }

  .modal-leave-active .modal-content {
    -webkit-transform: translate(0px, -20px);
    transform: translate(0px, -20px);
  }
</style>
