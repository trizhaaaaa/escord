<template>
<transition name="modal-fade">
  <div class="modal-backdrop">
    <div class="modal">

      <!-- Header -->
      <header class="modal-header">
         <h1>Add Student</h1>
      </header>

     

      <!-- Body -->
      <section class="modal-body">

          <div class="body-content">

              <div class="stud-id">
                  <label for="studID" class="input__label">Student Number</label>
                  <input type="text" name="studID" id="studID" class="input__text" maxlength="8" required>
              </div>

              <div class="stud-name-main">
                  
             <div class="stud-name _studLN">
                <label for="studLN" class="input__label">Last Name</label>
                <input type="text" name="studLN" id="studLN" maxlength="30" class="input__text" required>
             </div>

             <div class="stud-name _studFN">
                <label for="studFN" class="input__label">First Name</label>
                <input type="text" name="stuFN" id="studFN" maxlength="30" class="input__text" required>
             </div>

             <div class="stud-name _studMI">
                <label for="studMI" class="input__label">MI</label>
                <input type="text" name="studMI" id="studMI" maxlength="4" class="input__text">
             </div>

             </div>

          </div>

      </section>
      
      <!-- Footer -->
      <footer class="modal-footer">
         <p class="p__footer">Please review your inputs before proceeding.</p><br>
          <div class="footer-btn">
            <button
            type="button"
            class="btn-footer-cancel"
            @click="close"
            >
            Cancel
            </button>
            
            <button
            type="submit"
            class="btn-footer-add"
            @click="addgs"
            >
            Add Student
            </button>
          </div>
      </footer>

    </div>
  </div>
</transition>
</template>

<script>
export default {
  
  data(){
    return{
      
    }
  },

   methods:{
    close(){
      this.$emit('close');
      }
    }
}
</script>

<style scoped>
  
  .stud-id{
      display: flex;
      align-items: center;

      position: relative;
      margin-top: 2rem;
      
  }

  .stud-name-main {
      display: flex;
  }

  .stud-name {
      display: flex;
      align-items: center;

      position: relative;
      margin-top: 2.75rem;
  }

  ._studLN, ._studFN {
      flex: 2;
  }

  ._studMI{
      flex: 1;
  }

  .input__label {
      font-family: "Cuprum",sans-serif;
      text-align: left;
      font-size: 1rem;
      letter-spacing: 0.1rem;
      text-transform: uppercase;
      /* width: 10rem; */
      margin: 0 0.5rem;
      flex-shrink: 0;

      position: absolute;
      top: -1.5rem;
      left: 0.5rem;
  }

  .input__text {
      outline: none;
      flex: 1;
      margin: 0 0.5rem;
      width: 0;
      border-bottom: 1px solid #bdbdbd;
      border-radius: 5px;
      padding: 3px 0 3px 10px;
      box-sizing: border-box;
      color: #545454;
      text-transform: uppercase;
      font-weight: 600;
      letter-spacing: 0.1rem;

      margin-bottom: 0.25rem;
  }



/* modal */

  .p__text{
    float: left;
    margin-left: 20px;
    font-weight: bold;
    letter-spacing: 0.5rem;
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
    z-index: 99;
  }

  .modal {
    background: #FFFFFF;
    box-shadow: 2px 2px 20px 1px;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
    width: 95%;
    max-width: 25rem;
    height: 90%;
    max-height: 23.75rem;
    border-radius: 10px;
  }

  .modal-header,
  .modal-footer {
    padding: 15px;
    display: flex;
  }

  .modal-header {
    position: relative;
    border-bottom: 1px solid #cccccc;
    color: #545454;
    text-shadow: 2px 2px 5px #ff9807;
    justify-content: center;
  }

  .modal-footer {
    border-top: 1px solid #cccccc;
    flex-direction: column;
    justify-content: flex-end;

    margin-top: 0.5rem;
  }

  .footer-btn{
    margin-top: 5px;
  }

  .modal-body {
    position: relative;
    padding: 20px 10px;
  }

  .btn-footer-cancel {
    color: #545454;
    background: #fff;
    border: 2px solid #545454;
    border-radius: 10px;
    padding: 7px 10px;
    margin-right: 1rem;
    transition-duration: 0.3s;
  }

  .btn-footer-cancel:hover{
    background: #545454;
    color: #fff;
  }

  .btn-footer-add {
    color: #545454;
    font-weight: 600;
    background: #ff9807aa;
    border: 2px solid #ff9807aa;
    border-radius: 10px;
    padding: 7px 10px;
  }

   .btn-footer-add:hover{
    background: #ff9807;
    box-shadow: 2px 2px 10px 1px #dadada;
  }

  .modal-fade-enter, 
  .modal-fade-leave-to{
    opacity: 0;
  }

  .modal-fade-enter-active, 
  .modal-fade.leave-active{
    transition: opacity 0.5s ease;
  }

  .p__footer{
    font-size: 0.8rem;
    font-weight: 600;
    letter-spacing: 0.1rem;
    color: #2d2d2d;
    background: #ff98077e;
    padding: 5px 0;
  }

  /* scrollbar */

::-webkit-scrollbar{
  width: 15px;
}

::-webkit-scrollbar-thumb{
  background: #ff9807aa;
  background-clip: padding-box;
  border-radius: 25px;
}

::-webkit-scrollbar-thumb:hover{
  background: #ff9807;
}


</style>