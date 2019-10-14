<template>
  <div>
    <div class="page-container">
      <el-row type="flex" justify="center">
        <el-col :xs="24" :sm="24" :lg="16">
          <!-- Announcement -->
          <el-card :shadow="'never'" class="card">
            <div slot="header" class="clearfix">
              <span>Announcement</span>
            </div>
            <p>
              All steps of the application should be completed as requirement for the admission test.
              You may save each section and come back to complete your application.
            </p>
          </el-card>

          <!-- Basic Information -->

          <el-card :shadow="'never'" class="card">
            <div slot="header" class="clearfix">
              <span>CV and Portfolio</span>
            </div>

            <el-form
              ref="form"
              :model="form"
              label-width="120px"
              :label-position="setup.labelPosition"
            >
              <el-form-item label="CV File">
                <el-upload
                  class="upload-cv"
                  drag
                  action="https://jsonplaceholder.typicode.com/posts/"
                  :on-preview="handlePreview"
                  :on-remove="handleRemove"
                  :file-list="fileList"
                  multiple
                >
                  <i class="el-icon-upload" />
                  <div class="el-upload__text">
                    Drop file here or
                    <em>click to upload</em>
                  </div>
                  <div
                    slot="tip"
                    class="el-upload__tip"
                  >Your CV should consists of Personal details, Professional Summary, Education, Working Experience, Skills/Interests</div>
                </el-upload>
              </el-form-item>
              <el-form-item label="LinkedIn Profile">
                <el-input v-model="form.linkedIn" placeholder="http://" />
              </el-form-item>
              <el-form-item label="Link Portfolio 1">
                <el-input v-model="form.portfolio1" placeholder="http://" />
              </el-form-item>
              <el-form-item label="Link Portfolio 2">
                <el-input v-model="form.portfolio2" placeholder="http://" />
              </el-form-item>
              <el-form-item label="Link Portfolio 3">
                <el-input v-model="form.portfolio3" placeholder="http://" />
              </el-form-item>
              <el-form-item label="Link Portfolio 4">
                <el-input v-model="form.portfolio4" placeholder="http://" />
              </el-form-item>
              <el-form-item label="Link Portfolio 5">
                <el-input v-model="form.portfolio5" placeholder="http://" />
              </el-form-item>
            </el-form>
          </el-card>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
// import DropdownMenu from "@/components/Share/DropdownMenu";

export default {
  name: 'CVPortfolio',
  components: {},
  data() {
    return {
      setup: {
        labelPosition: 'top'
      },
      Model: {
        username: '',
        email: '',
        firstName: '',
        lastName: '',
        address: '',
        city: '',
        country: '',
        zipCode: '',
        about: ''
      },
      form: {
        type: []
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.page-container {
  background-color: #f6f6f6;
  padding: 36px;

  .card {
    padding: 24px;
    margin-bottom: 32px;
  }
}
</style>
