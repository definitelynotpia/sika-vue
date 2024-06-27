<template>
    <div class="d-flex flex-column justify-center align-center">
        <div class="ma-4 border-lg border-surface-variant rounded-0" style="background: white;">
            <!-- color value, opacity -->
            <v-color-picker v-model="color" hide-canvas hide-inputs style="margin-left: -25px; margin-bottom: -15px;"
                class="rounded-0" width="800" elevation="0" color="transparent"></v-color-picker>
            <!-- brush width -->
            <v-slider v-model="strokeWidth" :max="max" :min="min" class="mx-13 mb-2 align-center" step="1" thumb-label hide-details>
                <template v-slot:append>
                    <v-text-field v-model="strokeWidth" density="compact" :max="max" :min="min" style="width: 80px" type="number" hide-details single-line></v-text-field>
                </template>
            </v-slider>
            <!-- color swatches -->
            <v-flex v-for="swatch in swatches" :key="swatch">
                <v-btn v-on:click="color = swatch" :color="swatch" height="40" class="mb-2 mx-1 rounded-0 border-lg"></v-btn>
            </v-flex>
        </div>

        <canvas ref="canvas" id="drawing-pad" @mousedown="startPainting" @mouseup="finishedPainting" @mousemove="draw"
            class="rounded-0 border-lg" width="800" height="700"></canvas>

        <div class="d-flex flex-row justify-center">
            <v-btn size="large" @click="clearCanvas" color="red-lighten-3" class="my-4 mr-4 rounded-0">
                Clear
            </v-btn>
            <v-btn size="large" @click="exportArt" color="green-lighten-4" class="my-4 mr-4 rounded-0">
                Save
            </v-btn>
            <v-btn size="large" @click="replayArt" color="yellow-lighten-2" class="my-4 mr-4 rounded-0">
                Redraw
            </v-btn>
        </div>

        <img ref="img" src="" id="canvas-image" width="400" height="400" />
    </div>
</template>

<script>
export default {
    name: "HomeView",
    data: () => ({
        canvas: null,
        context: null,
        color: '#ff0000',
        isDrawing: false,
        startX: 0,
        startY: 0,
        strokeWidth: 5,
        min: 1,
        max: 200,
        swatches: [
            '#000000',
            '#808080',
            '#ffffff',
            '#e81416',
            '#ffa500',
            '#faeb36',
            '#79c314',
            '#487de7',
            '#4b369d',
            '#70369d',
        ],
        points: [],
    }),
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
                var startX = vm.startX;
                var startY = vm.startY;
                var strokeWidth = this.strokeWidth;

                vm.context.beginPath();
                vm.context.moveTo(startX, startY);
                vm.context.lineTo(x, y);
                vm.context.lineWidth = strokeWidth;
                vm.context.lineCap = 'round';
                vm.context.strokeStyle = color;
                vm.context.stroke();

                vm.startX = x;
                vm.startY = y;
                vm.points.push({
                    startX: startX,
                    startY: startY,
                    x: x,
                    y: y,
                    color: color,
                    strokeWidth: strokeWidth,
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
                var startX = vm.points[index].startX;
                var startY = vm.points[index].startY;
                var x = vm.points[index].x;
                var y = vm.points[index].y;
                var strokeColor = vm.points[index].color;
                var strokeWidth = vm.points[index].strokeWidth;

                vm.context.beginPath();
                vm.context.moveTo(startX, startY);
                vm.context.lineTo(x, y);
                vm.context.lineWidth = strokeWidth;
                vm.context.lineCap = 'round';
                vm.context.strokeStyle = strokeColor;
                vm.context.stroke();
            }
        },
    },
}
</script>

<style lang="scss">
$color-picker-swatch-color-height: 50px;
$color-picker-swatch-color-width: 25px;
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