<template>
    <div>
        <svg class="input-border-left" :height="height" width="3" 
            :style="{
                strokeDasharray:height,
                strokeDashoffset:heightCon
                }">
	        <path :d="'M 0 0 l 0 ' + height" stroke-width="3" fill="none" />
        </svg>
        <svg class="input-border-top" height="3" :width="width"
            :style="{
                strokeDasharray:width,
                strokeDashoffset:widthCon
                }">
	        <path :d="'M 0 0 l ' + width + ' 0'" stroke-width="3" fill="none" />
        </svg>        
        <svg class="input-border-right" :height="height" width="3"
            :style="{
                strokeDasharray:height,
                strokeDashoffset:heightCon
                }">>
	        <path :d="'M 0 ' + height + ' l 0 -' + height" stroke-width="3" fill="none" />
        </svg>
        <svg class="input-border-bottom" height="3" :width="width"
            :style="{
                strokeDasharray:width,
                strokeDashoffset:widthCon
                }">
	        <path :d="'M ' + width + ' 0 l -' + width + ' 0'" stroke-width="3" fill="none" />
        </svg>
    </div>
</template>
<script>
export default {
    props:['animate', 'height', 'width'],
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
    }
}
</script>

<style scoped>
    .input-border-left, .input-border-top, .input-border-right, .input-border-bottom{        
        z-index: 1;
        position: absolute;
        stroke: rgb(118, 161, 255)
    }
    .input-border-left{
        top:0;
        left: 0;
    }
    .input-border-top{
        top:0;
        left: 0;
    }
    .input-border-right{
        top:0;
        right: -1px;
    }
    .input-border-bottom{        
        bottom:-2px;
        left: 0;
    }
    .input-border-left, .input-border-right{
        transition: .3s
    }
    .input-border-bottom, .input-border-top{
        transition: .3s
    }
</style>
