<script setup>
import UploadLayout from '~/layouts/UploadLayout.vue';

let file = ref(null)
let fileDisplay = ref(null)
let errorType = ref(null)
let caption = ref('')
let fileData = ref(null)
let errors = ref(null)
let isUploading = ref(false)

watch(() => caption.value, (caption) => {
  if (caption.length >= 150) {
    errorType.value = 'caption'
    return
  }

  errorType.value = null
})

const onDrop = (e) => {
  errorType.value = ''
  file.value = e.dataTransfer.files[0]
  fileData.value = e.dataTransfer.files[0]

  let extension = file.value.name.substring(file.value.name.lastIndexOf('.') + 1)

  if (extension !== 'mp4') {
    errorType.value = 'file'
    return
  }

  fileDisplay.value = URL.createObjectURL(e.dataTransfer.files[0])
}

const onChange = () => {
  fileDisplay.value = URL.createObjectURL(file.value.files[0])
  fileData.value = file.value.files[0]
}

const discard = () => {
  fileDisplay.value = null
  fileData.value = null
  file.value = null
  caption.value = ''
}

const clearVideo = () => {
  fileDisplay.value = null
  fileData.value = null
  file.value = null
}
</script>

<template>
  <UploadError :errorType="errorType" />

  <UploadLayout>
    <div class="w-full mt-[80px] mb-[40px] bg-white shadow-lg rounded-md py-6 md:px-10 px-4">
      <div>
        <div class="text-[23px] font-semibold">Upload Video</div>
        <div class="text-gray-400 mt-1">Post a video to your account</div>
      </div>

      <div class="mt-8 md:flex gap-6">
        <label v-if="!fileDisplay" for="fileInput" @drop.prevent="onDrop" @dragover.prevent="$event => $event.preventDefault()"
               class="md:mx-0 mx-auto mt-4 mb-6 flex flex-col items-center justify-center w-full max-w-[260px] h-[470px] text-center p-3 border-2 border-dashed border-gray-300 rounded-lg hover:bg-gray-100 cursor-pointer">
          <Icon name="majesticons:cloud-upload" size="40" color="#b3b3b1"/>
          <div class="mt-4 text-[17px]">Select video to upload</div>
          <div class="mt-1.5 text-gray-500 text-[13px]">Or drag and drop a file</div>
          <div class="mt-12 text-gray-400 text-sm">MP4</div>
          <div class="mt-2 text-gray-400 text-[13px]">Up to 30 minutes</div>
          <div class="mt-2 text-gray-400 text-[13px]">Less than 2 GB</div>
          <div class="px-2 py-1.5 mt-8 text-white text-[15px] w-[80%] bg-[#f02c56] rounded-sm">
            Select file
          </div>
          <input @input="onChange" type="file" ref="file" id="fileInput" hidden accept=".mp4"> </label>
        <div v-else
             class="md:mx-0 mx-auto mt-4 md:mb-12 mb-16 flex items-center justify-center w-full max-w-[260px] h-[540px] p-3 rounded-2xl cursor-pointer relative">
          <div class="bg-black h-full w-full rounded-3xl">
            <img src="/assets/images/mobile-case.png" class="absolute z-20 pointer-events-none">
            <img src="/assets/images/tiktok-logo-white.png" class="absolute right-4 bottom-6 z-20" width="90">
            <video autoplay loop muted class="absolute rounded-xl object-cover z-10 p-[13px] w-full h-full"
                   :src="fileDisplay">
            </video>
            <div
              class="absolute -bottom-12 flex items-center justify-between z-50 rounded-xl border w-full p-2 border-gray-300">
              <div class="flex items-center truncate">
                <Icon name="clarity:success-standard-line" size="16" class="min-w-[16px]"/>
                <div class="text-[11px] pl-1 truncate text-ellipsis">{{ fileData.name }}</div>
              </div>
              <button @click="$event => clearVideo()" class="text-[11px] ml-2 font-semibold">Change</button>
            </div>
          </div>
        </div>
        <div class="mt-4 mb-6">
          <div class="flex bg-[#f8f8f8] py-4 px-6">
            <div>
              <Icon class="mr-4" size="20" name="mdi:box-cutter-off"/>
            </div>
            <div>
              <div class="text-semibold text-[15px] mb-1.5">Divider videos and edit</div>
              <div class="text-semibold text-[13px] text-gray-400">
                You can divide your videos into multiple parts and edit them individually,
                remove redundant parts, and turn landscape videos into portrait videos.
              </div>
            </div>
            <div class="flex justify-end max-w-[130px] w-full h-full text-center my-auto">
              <button class="px-8 py-1.5 text-white text-[15px] bg-[#f02c56] rounded-sm">
                Edit
              </button>
            </div>
          </div>
          <div class="mt-5">
            <div class="flex items-center justify-between">
              <div class="mb-1 text-[15px]">Caption</div>
              <div class="text-gray-400 text-[12px]">{{ caption.length }}/150</div>
            </div>
            <input v-model="caption" maxlength="150" type="text" class="w-full border p-2.5 rounded-md focus:outline-none">
          </div>
          <div class="flex gap-3">
            <button @click="$event => discard()" class="px-10 py-2.5 mt-8 border text-[16px] hover:bg-gray-100 rounded-sm">Discard</button>
            <button class="px-10 py-2.5 mt-8 border text-[16px] text-white bg-[#f02c56] rounded-sm">Post</button>
          </div>
        </div>
      </div>
    </div>
  </UploadLayout>
</template>
