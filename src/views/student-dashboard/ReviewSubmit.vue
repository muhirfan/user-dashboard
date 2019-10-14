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
              <span>Motivational Letter</span>
            </div>

            <el-form
              ref="form"
              :model="form"
              label-width="120px"
              :label-position="setup.labelPosition"
            >
              <el-form-item label="Motivational Letter">
                <el-input
                  v-model="form.motivationalLetter"
                  type="textarea"
                  :autosize="{ minRows: 4, maxRows: 8}"
                  placeholder="In 300 words or more, please tell us why you would want to join The Apple Developer Academy @ Infinite Learning."
                />
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
  name: 'ReviewSubmit',
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
