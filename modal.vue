<template>
  <div>
    <button @click="activeModal = true">Abrir Modal</button>
    <transition name="modal">
      <section v-if="activeModal" class="modal" @click="clickForaModal">
        <div class="modal-container">
          <div class="modal-header">
            <h1>Modal</h1>
            <span class="modal-close" @click="activeModal = false">X</span>
          </div>
          <div class="modal-body">
            <h4>Loren</h4>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur voluptatum nam facilis reiciendis eius, natus, exercitationem, repellendus numquam nobis illum quam quos placeat omnis minima et iusto nihil at tempora!
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam sint enim dolores, ipsam et at quos nam debitis perferendis, nemo obcaecati mollitia magnam, ab ratione? Modi expedita dicta dignissimos excepturi.
          </div>
          <div class="modal-footer"></div>
        </div>
      </section>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeModal: false
    }
  },
  methods: {
    clickForaModal(event) {
      if(event.target === event.currentTarget) {
        this.activeModal = false;
      }
    }
  }
}
</script>

<style>

.modal {
  position: absolute;
  background: rgba(1, 1,1, .6);
  top: 0;
  left: 0;
  right: 0;
  height: 100%;
  width: 100%;
  overflow-y: scroll;
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal-container {
  padding: 20px;
  background: white;
  width: 500px;
  animation: slideIn .3s forwards;
}

.modal-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.modal-close {
  font-weight: bold;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  font-size: 1.5rem;
  cursor: pointer;
}

.modal-enter, .modal-leave-to {
  opacity: 0;
}

.modal-enter-active, .modal-leave-to {
  transition: opacity .3s;
}

.v-leave-active {
animation: fadeDown .3s forwards;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translate3d(0, -20px, 0);
  }
  
  to {
    opacity: 1;
    transform: translate3d(0, 0px, 0);
  }
}

@keyframes fadeInDown {
  from {
    transform: translate3d(0, -30px, 0);
    opacity: 0;
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0px, 0);
  }
}
</style>