<template>
  <div>
    <nav
      class="navbar navbar-expand-lg navbar-light bg-light fixed-top p-st"
      :class="{
        'bg-light': !nightMode,
        'navbar-blur': navbarConfig.blur,
        'bg-dark2': nightMode,
      }"
    >
      <div class="container">
        <a
          class="navbar-brand"
          href="/"
          @click.prevent="$emit('scroll', 'home')"
        >
          <Logo :nightMode="nightMode" />
        </a>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span style="color: gray; font-size: 23px;"
            ><i class="fas fa-bars"></i>
            </span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav ml-auto">
            <li class="nav-item mx-2">
              <a
                class="nav-link"
                href="#privacy-policy"
                @click.prevent="() => showModalFn(privacyPolicy)"
                :class="{ 'text-light': nightMode }"
                >Privacy Policy</a>
            </li>
            <li class="nav-item ml-2">
              <a
                class="nav-link"
                href="#"
                @click.prevent="switchMode"
                :class="{ 'text-light': nightMode }"
                ><i
                  :class="{
                    'fas fa-moon': nightMode,
                    'far fa-moon': !nightMode,
                  }"
                  v-tooltip.bottom="nightMode ? 'Light Mode' : 'Night Mode'"
                ></i
              ></a>
            </li>
          </ul>
        </div>
        <transition name="modal">
          <Modal
            :showModal="showModal"
            @close="closeModal"
            v-if="showModal"
            :modal_info="modal_info"
            :nightMode="nightMode"
          />
        </transition>
      </div>
    </nav>
  </div>
</template>

<script>
import Logo from "./helpers/Logo";
import info from "../../info";
import Modal from "./helpers/Modal";

export default {
  name: "Navbar",
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      navbarConfig: info.config.navbar,
      localNightMode: this.nightMode,
      privacyPolicy: info.privacyPolicy,
      showModal: false,
      modal_info: {},
    };
  },
  components: {
    Logo,
    Modal,
  },
  methods: {
    switchMode() {
      this.localNightMode = !this.localNightMode;
      this.$emit("nightMode", this.localNightMode);
    },
    showModalFn(privacyPolicy) {
      this.showModal = !this.showModal;
      this.modal_info = privacyPolicy;
      this.$emit("showModal", this.showModal);
    },
    closeModal() {
      this.showModal = false;
      document.getElementsByTagName("body")[0].classList.remove("modal-open");
    },
  },
};
</script>

<style scoped>
.nav-link {
  font-weight: 500;
}
.nav-link:hover{
  background-color: rgba(160, 159, 159, 0.336);
}
.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

button {
  border: none;
  outline: none;
}

button:hover {
  border: none;
  outline: none;
}

nav {
  border-bottom: 1px solid rgba(160, 159, 159, 0.336);
  position: fixed !important;
}

.navbar-blur {
  background-color: #ffffff7e;
  backdrop-filter: blur(12px);
}
</style>
