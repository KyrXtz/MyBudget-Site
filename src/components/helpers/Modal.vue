<template>
    <div>
      <div class="modal-mask">
        <div class="modal-wrapper">
          <div
            class="modal-container"
            :class="{
              'bg-light': !nightMode,
              'bg-dark': nightMode,
              'text-light': nightMode,
            }"
          >
            <div class="title1 pb-2 pheight pt-1 px-4 pt-3">
              {{modal_info}}                       
            </div>
  
            <div class="text-center pb-3">
              <hr
                class="mt-1 mb-3"
                :class="{ pgray: !nightMode, 'bg-secondary': nightMode }"
              />              
              <button class="btn w-25" @click="$emit('close')">close</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  
  export default {
    name: "Modal",
    components: {
    },
    props: {
      showModal: {
        type: Boolean,
      },
      modal_info: {
        type: String,
      },
      nightMode: {
        type: Boolean,
      },
    },
    created() {
      document.getElementsByTagName("body")[0].classList.add("modal-open");
    },
    methods: {
      open(url) {
        window.open(url, "_blank");
      },
    },
  };
  </script>
  
  <style scoped>
  body.modal-open {
    overflow: hidden;
  }
  
  a {
    text-decoration: none;
    color: black;
    transition: all 0.2s;
    cursor: pointer;
  }
  
  a:hover {
    transition: all 0.2s;
    color: gray;
  }
  .pheight {
    height: 600px;
    overflow: auto;
    text-align: justify;
  }
  .date {
    font-size: 14px;
    font-weight: 400;
  }
  .modal-mask {
    position: fixed;
    z-index: 9998;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    transition: opacity 0.5s ease;
  }
  
  .modal-wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }
  
  .modal-container {
    width: 40%;
    max-height: 70%;
    margin: 0px auto;
    border-radius: 7px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
    transition: all 0.3s ease;
    flex-direction: column;
    display: flex; /*added*/
  }
  
  @media screen and (max-width: 1600px) {
    .modal-container {
      width: 60%;
    }
  }
  
  @media screen and (max-width: 1200px) {
    .modal-container {
      width: 80%;
    }
  }
  
  @media screen and (max-width: 580px) {
    .modal-container {
      width: 90%;
    }
  }
  
  .modal-body {
    margin: 20px 0;
    overflow-y: scroll;
    max-height: inherit;
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
  
  .title {
    font-size: 30px;
    font-weight: 500;
  }
  .title1 {
    font-size: 24px;
    font-weight: 400;
  }
  
  .title2 {
    font-size: 20px;
    font-weight: 400;
  }
  
  .title3 {
    font-size: 16px;
    font-weight: 400;
  }
  
  .badge {
    background-color: #bbd4dd;
    transition: all 0.5s;
    font-weight: 500;
  }
  
  .badge:hover {
    transition: all 0.5s;
    box-shadow: 2px 2px 5px rgb(179, 179, 179);
  }
  
  .btn {
    border-color: #759CC9;
    color: #759CC9;
  }
  
  .btn:hover {
    background-color: #759CC9;
    border-color: #759CC9;
    color: white;
  }
  
  .btn:focus {
    background-color: #759CC9;
    border-color: #759CC9;
    color: white;
  }
  
  .bg-dark4 {
    background-color: #494e55 !important;
  }
  </style>
  