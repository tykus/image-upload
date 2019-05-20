<template>
    <div class="dropzone">
        <div class="dz-preview dz-file-preview" ref="previewTemplate">
            <div class="dz-details">
                <div class="dz-filename"><span data-dz-name></span></div>
                <div class="dz-size" data-dz-size>Fuck you</div>
                <img data-dz-thumbnail />
            </div>
            <div class="dz-progress"><span class="dz-upload" data-dz-uploadprogress></span></div>
            <div class="dz-success-mark"><span>✔</span></div>
            <div class="dz-error-mark"><span>✘</span></div>
            <div class="dz-error-message"><span data-dz-errormessage></span></div>
        </div>
    </div>
</template>

<script>
import Dropzone from 'dropzone'
export default {
    props: {
        url: String,
        name: String,
        method: {
            type: String,
            required: false,
            default: 'POST'
        }
    },
    mounted () {
        let vm = this
        Dropzone.autoDiscover = false
        new Dropzone(this.$el, {
            url: this.url,
            method: this.method,
            thumbnail: function(file, dataUrl) {
                return
            },
            // createImageThumbnails: false, // todo this is not working...
            // thumbnailWidth: 80,
            // thumbnailHeight: 80,
            // previewTemplate: previewTemplate,
            // previewsContainer: "#previews", // Define the container to display the previews
            // clickable: ".fileinput-button", // Define the element that should be used as click trigger to select files.
            init: function () {
                this.on("addedfile", function (file) {
                    vm.$emit('file-added', file)
                })
            }
        })
    }
}
</script>

<style scoped>
    @import './../../node_modules/dropzone/dist/dropzone.css';

    .dz-preview,
    .dz-file-preview,
    .dz-processing,
    .dz-error 
    .dz-complete {
        display: none
    }
 </style>