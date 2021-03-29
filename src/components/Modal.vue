<template>
    <transition name="modal-fade">
        <div class="modal-backdrop">
            <div class="modal">
            <header class="modal-header">
                <button
                type="button"
                class="btn-close"
                @click="close"
                >
                x
                </button>
            </header>

            <section class="modal-body">
              <h2>{{strDrink}}</h2>
              <h3>Ingredients:</h3>
              <p>{{strMeasure1 + " " + strIngredient1}}</p>
              <p>{{strMeasure2 + " " + strIngredient2}}</p>
              <p>{{strMeasure3 + " " + strIngredient3}}</p>
              <p>{{strInstructions}}</p>
            </section>

            <footer class="modal-footer">
                <button
                type="button"
                class="btn-green"
                @click="close"
                >
                Close
                </button>
            </footer>
            </div>
        </div>
    </transition>
</template>

<script>
  export default {
    name: 'Modal',
    props: {
        msg: String,
        strDrink: String,
        strMeasure1: String,
        strMeasure2: String,
        strMeasure3: String,
        strIngredient1: String,
        strIngredient2: String,
        strIngredient3: String,
        strInstructions: String
    },
    methods: {
      close() {
        this.$emit('close');
      },
    },
  };
</script>

<style>
  p {
    font-size: 14pt;
    padding: 10px;
  }

  h2 {
    padding: 10px;
  }

  h3 {
    padding: 10px;
  }

  .modal-backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal {
    background: #FFFFFF;
    box-shadow: 2px 2px 20px 1px;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
  }

  .modal-header,
  .modal-footer {
    padding: 15px;
    display: flex;
  }

  .modal-header {
    position: relative;
    border-bottom: 1px solid #eeeeee;
    color: #4AAE9B;
    justify-content: space-between;
  }

  .modal-footer {
    border-top: 1px solid #eeeeee;
    flex-direction: column;
    justify-content: flex-end;
  }

  .modal-body {
    position: relative;
    padding: 20px 10px;
  }

  .btn-close {
    position: absolute;
    top: 0;
    right: 0;
    border: none;
    font-size: 20px;
    padding: 10px;
    cursor: pointer;
    font-weight: bold;
    color: #0065ad;
    background: transparent;
  }

  .btn-green {
    color: white;
    background: #0065ad;
    border: 1px solid #0065ad;
    border-radius: 2px;
    padding: 10px;
  }

  .modal-fade-enter,
  .modal-fade-leave-to {
    opacity: 0;
  }

  .modal-fade-enter-active,
  .modal-fade-leave-active {
    transition: opacity .5s ease;
  }
</style>