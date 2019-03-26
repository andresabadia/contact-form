<template>
    <div>
        <svg class="input-border-left" :height="height" width="3"
            :style="{
                strokeDasharray:height,
                strokeDashoffset:heightCon
                }">
	        <path :d="'M 0 '+rnd1+' l 0 -'+rnd1+''" stroke-width="3" fill="none" />
        </svg>
        <svg class="input-border-top" height="3" :width="width"
            :style="{
                strokeDasharray:width,
                strokeDashoffset:widthCon
                }">
	        <path :d="'M '+rnd2+' 0 l -'+rnd2+' 0'" stroke-width="3" fill="none" />
        </svg>   
        <svg class="input-border-top" height="3" :width="width+10"
            :style="{
                strokeDasharray:width,
                strokeDashoffset:widthCon
                }">
	        <path :d="'M '+(width+10)+' 0 l -'+rnd3+' 0'" stroke-width="3" fill="none" />
        </svg>       
        <svg class="input-border-right" :height="height" width="3"
            :style="{
                strokeDasharray:height,
                strokeDashoffset:heightCon
                }">
	        <path :d="'M 0 ' + (height-rnd4) + ' l 0 '+rnd4+''" stroke-width="3" fill="none" />
        </svg>
        <svg class="input-border-bottom" height="3" :width="width"
            :style="{
                strokeDasharray:width,
                strokeDashoffset:widthCon
                }">
	        <path :d="'M '+rnd5+' 0 l '+(width-rnd5)+' 0'" stroke-width="3" fill="none" />
        </svg>
    </div>
</template>
<script>
export default {
    props:['animate', 'height', 'width'],
    data(){
        return{
            tmp:0,
            rnd1:0,
            rnd2:0,
            rnd3:0
        }
    },
    created(){
        this.random(this.height*0.3, this.height*0.75)
        this.rnd1=this.tmp        
        this.random(this.width*0.1, this.width*0.3)
        this.rnd2=this.tmp
        this.random(this.width*0.1, this.width*0.5)
        this.rnd3=this.tmp
        this.random(this.height*0.3, this.height*0.75)
        this.rnd4=this.tmp  
        this.random(this.width*0.5, this.width*0.9)
        this.rnd5=this.tmp
    },
    computed:{
        heightCon() {
            if(!this.animate){
                return this.height
                }
            return 0
        },
        widthCon() {
            if(!this.animate){
                return this.width
            }
            return 0
        }
    },
    methods:{
        random(min, max){
            this.tmp = Math.floor(Math.random() * (max - min) ) + min;
        }
    }
}
</script>

<style scoped>
    .input-border-left, .input-border-top, .input-border-right, .input-border-bottom{        
        z-index: 1;
        position: absolute;
        stroke: rgba(118, 161, 255, 0.562);
    }
    .input-border-left{
        top:-5px;
        left: 0;
    }
    .input-border-top{
        top:0;
        left: -10px;
    }
    .input-border-right{
        top:10px;
        right: -1px;
    }
    .input-border-bottom{        
        bottom:-2px;
        left: 5px;
    }
    .input-border-left, .input-border-right{
        transition: .5s
    }
    .input-border-bottom, .input-border-top{
        transition: .5s
    }
    .input-border-animation{        
        stroke-dashoffset: 0;
    }
</style>
