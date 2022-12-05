<template>
  <img class="image" data-index="0" data-status="inactive" src="https://images.unsplash.com/photo-1670148570351-601dd7bebcd6?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80"/>
  <img class="image" data-index="1" data-status="inactive" src="https://images.unsplash.com/photo-1669979901449-581e018c012b?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=776&q=80"/>
  <img class="image" data-index="2" data-status="inactive" src="https://images.unsplash.com/photo-1669926504091-2735b6cb51a7?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80"/>
  <img class="image" data-index="3" data-status="inactive" src="https://images.unsplash.com/photo-1670173485940-a112bceb9970?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80"/>
  <img class="image" data-index="4" data-status="inactive" src="https://images.unsplash.com/photo-1670168173015-9b014630f5c2?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80"/>
  <img class="image" data-index="5" data-status="inactive" src="https://plus.unsplash.com/premium_photo-1670027491344-9cc9130aa001?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=798&q=80"/>
  <img class="image" data-index="6" data-status="inactive" src="https://images.unsplash.com/photo-1670176055415-bb70b32a9b18?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=970&q=80"/>
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
      globalIndex:0,
      last:{
        x:0,
        y:0
      }
    }
  },
  mounted() {
    const images = document.getElementsByClassName("image");
    const activate = (image,x,y)=>{
      image.style.left= `${x}px`;
      image.style.top= `${y}px`;
      image.dataset.status = "active";
      image.style.zIndex = this.globalIndex;
      this.last = {x,y};
    };
    const distanceFromLast = (x,y) =>{
      return Math.hypot(x-this.last.x,y-this.last.y);
    }
    window.onmousemove = e =>{
      if(distanceFromLast(e.clientX,e.clientY) > 100){
      const lead = images[this.globalIndex % images.length ],
            tail = images[(this.globalIndex-5) % images.length ];
      activate(lead,e.clientX,e.clientY);
      if(tail) tail.dataset.status = "inactive";
      this.globalIndex++;

      console.log( this.globalIndex );
      }
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
  transition: opacity .2s linear;
}
.image[data-status="inactive"]{
  opacity: 0;
}
.image[data-status="active"]{
  opacity: 1;
}
</style>
