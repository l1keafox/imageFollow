<template>
  <img class="image" data-index="0" data-status="inactive" src="https://source.unsplash.com/random"/>
  <img class="image" data-index="1" data-status="inactive"  src="https://source.unsplash.com/random"/>
  <img class="image" data-index="2" data-status="inactive" src="https://source.unsplash.com/random"/>
  <img class="image" data-index="3" data-status="inactive" src="https://source.unsplash.com/random"/>
  <img class="image" data-index="4" data-status="inactive" src="https://source.unsplash.com/random"/>
  <img class="image" data-index="5" data-status="inactive" src="https://source.unsplash.com/random"/>
  <img class="image" data-index="6" data-status="inactive" src="https://source.unsplash.com/random"/>
  <img class="image" data-index="7" data-status="inactive" src="https://images.unsplash.com/photo-1670161599938-3c143c778231?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=796&q=80"/>
  <img class="image" data-index="8" data-status="inactive" src="https://images.unsplash.com/photo-1670140274562-2496ccaa5271?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80"/>
  <img class="image" data-index="9" data-status="inactive" src="https://images.unsplash.com/photo-1669926468703-3bd11bad8609?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80"/>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data(){
    return{
      globalIndex:0
    }
  },
  mounted() {
    const images = document.getElementsByClassName("image");
    const activate = (image,x,y)=>{
      image.style.left= `${x}px`;
      image.style.top= `${y}px`;
      image.dataset.status = "active";
    };
    window.onmousemove = e =>{
      const lead = images[this.globalIndex% images.length ];
      activate(lead,e.clientX,e.clientY);
      this.globalIndex++;
    }
  },
}
</script>

<style>
body{
  background-color: rgb(10,10,10);
  height: 100vh;
  margin:0px;
  overflow:hidden;
}
.image{
  width: 50vmin;
  position: absolute;
  transform: translate(-50%,-50%);
}
.image[data-status="inactive"]{
  display:none;
}
.image[data-status="active"]{
  display:block;
}
</style>
