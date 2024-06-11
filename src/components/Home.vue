<template>
    <div id="app">
        <h1>Home</h1>

        <div class="color-picker">
            <v-color-picker v-model="color" hide-canvas hide-sliders show-swatches hide-inputs
                width="800"></v-color-picker>
        </div>

        <canvas ref="canvas" id="drawing-pad" @mousedown="startPainting" @mouseup="finishedPainting" @mousemove="draw"
            width="800" height="700"></canvas>

        <div>
            <v-btn variant="tonal" size="large" @click="clearCanvas" color="danger">
                <svg-icon type="mdi" :path="mdiDelete"></svg-icon>
            </v-btn>
            <v-btn variant="tonal" size="large" @click="exportArt">
                <svg-icon type="mdi" :path="mdiExportVariant"></svg-icon>
            </v-btn>
            <v-btn variant="tonal" size="large" @click="replayArt">
                <svg-icon type="mdi" :path="mdiPlay"></svg-icon>
            </v-btn>
        </div>

        <img ref="img" src="" id="canvas-image" width="400" height="400" />
    </div>
</template>

<script>
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiDelete, mdiPlay, mdiExportVariant } from '@mdi/js'

export default {
    name: "LoginView",
    components: {
        SvgIcon
    },
    data() {
        return {
            canvas: null,
            context: null,
            color: "#000000",
            isDrawing: false,
            startX: 0,
            startY: 0,
            points: [],
            // icons
            mdiDelete: mdiDelete,
            mdiPlay: mdiPlay,
            mdiExportVariant: mdiExportVariant,
        }
    },
    mounted() {
        var vm = this
        vm.canvas = vm.$refs.canvas;
        vm.context = vm.canvas.getContext("2d");
        vm.canvas.addEventListener("mousedown", vm.mousedown);
        vm.canvas.addEventListener("mousemove", vm.mousemove);
        document.addEventListener("mouseup", vm.mouseup);
    },
    methods: {
        mousedown(e) {
            var vm = this;
            var rect = vm.canvas.getBoundingClientRect();
            var x = e.clientX - rect.left;
            var y = e.clientY - rect.top;

            vm.isDrawing = true;
            vm.startX = x;
            vm.startY = y;
            vm.points.push({
                x: x,
                y: y,
            });
        },
        mousemove(e) {
            var vm = this;
            var color = this.color;
            var rect = vm.canvas.getBoundingClientRect();
            var x = e.clientX - rect.left;
            var y = e.clientY - rect.top;

            if (vm.isDrawing) {
                vm.context.beginPath();
                vm.context.moveTo(vm.startX, vm.startY);
                vm.context.lineTo(x, y);
                vm.context.lineWidth = 5;
                vm.context.lineCap = 'round';
                vm.context.strokeStyle = color;
                vm.context.stroke();

                vm.startX = x;
                vm.startY = y;
                vm.points.push({
                    x: x,
                    y: y,
                });
            }
        },
        mouseup() {
            var vm = this;
            vm.isDrawing = false;

            if (vm.points.length > 0) {
                localStorage["points"] = JSON.stringify(vm.points);
            }
        },
        clearCanvas() {
            var vm = this;
            var canvasWidth = vm.canvas.width;
            vm.canvas.width = canvasWidth;
            vm.points.length = 0;
        },
        exportArt() {
            var vm = this;
            var dataURL = vm.canvas.toDataURL();
            console.log(dataURL);
            var img = vm.$refs.img;
            img.src = dataURL;
        },
        replayArt() {
            var vm = this;
            var color = this.color;
            var canvasWidth = vm.canvas.width;
            vm.canvas.width = canvasWidth;

            if (vm.points.length === 0) {
                if (localStorage["points"] !== undefined) {
                    vm.points = JSON.parse(localStorage["points"]);
                }
            }

            var point = 1;
            setInterval(function () {
                drawNextPoint(point);
                point += 1;
            }, 10);

            function drawNextPoint(index) {
                if (index >= vm.points.length) {
                    return;
                }
                var startX = vm.points[index - 1].x;
                var startY = vm.points[index - 1].y;
                var x = vm.points[index].x;
                var y = vm.points[index].y;

                vm.context.beginPath();
                vm.context.moveTo(startX, startY);
                vm.context.lineTo(x, y);
                vm.context.lineWidth = 5;
                vm.context.lineCap = 'round';
                vm.context.strokeStyle = color;
                vm.context.stroke();
            }
        },
    },
}
</script>

<style>
* {
    box-sizing: border-box;
}

h2 {
    text-align: center;
    margin-bottom: 1rem;
}

canvas {
    display: block;
    background-color: #ffffff;
    border: 2px solid #333;
    border-radius: 5px;
    cursor: crosshair;
}

.color-box {
    display: inline-block;
    width: 20px;
    height: 20px;
    margin: 0 5px;
    cursor: pointer;
    border-radius: 50%;
}

.color-picker {
    display: flex;
    justify-content: center;
    margin-bottom: 1rem;
}

.clear-button {
    display: block;
    margin: 1rem auto;
    padding: 0.5rem 1rem;
    background-color: #333;
    color: #fff;
    text-align: center;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-weight: bold;
}

.clear-button:hover {
    background-color: #444;
}

img {
    border-style: solid;
}

img[src=""] {
    visibility: hidden;
    height: 0px;
}
</style>