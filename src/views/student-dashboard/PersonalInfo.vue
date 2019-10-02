<template>
  <div>
    <el-container>
      <el-header>Header</el-header>
      <el-main>
        <el-row :justify="center">
          <el-col :span="16">
            <!-- Announcement -->
            <h6 class="heading-small text-muted mb-4">Announcement</h6>
            <div class="pl-lg-4">
              <div class="row">
                <div class="col-md-12">
                  <p>
                    All steps of the application should be completed as requirement for the admission test.
                    You may save each section and come back to complete your application.
                  </p>
                </div>
              </div>
            </div>
            <hr class="my-4">
            <!-- Basic Information -->
            <h6 class="heading-small text-muted mb-4">Basic information</h6>
            <div class="pl-lg-4">
              <el-form
                ref="form"
                :model="form"
                label-width="120px"
                :label-position="setup.labelPosition"
              >
                <el-form-item label="Username">
                  <el-input v-model="form.username" />
                </el-form-item>
                <el-row :gutter="20">
                  <el-col :span="12">
                    <el-form-item label="First Name">
                      <el-input v-model="form.firstName" />
                    </el-form-item>
                  </el-col>
                  <el-col :span="12">
                    <el-form-item label="Last Name">
                      <el-input v-model="form.lastName" />
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-row :gutter="20">
                  <el-col :span="12">
                    <el-form-item label="Phone Number">
                      <el-input v-model="form.phoneNumber" />
                    </el-form-item>
                  </el-col>
                  <el-col :span="12">
                    <el-form-item label="Email Address">
                      <el-input v-model="form.email" />
                    </el-form-item>
                  </el-col>
                </el-row>
              </el-form>
            </div>
            <hr class="my-4">
            <!-- Personal Info -->
            <h6 class="heading-small text-muted mb-4">Personal info</h6>
            <div class="pl-lg-4">
              <el-form
                ref="form"
                :model="form"
                label-width="120px"
                :label-position="setup.labelPosition"
              >
                <el-row :gutter="20">
                  <el-col :span="12">
                    <el-form-item label="Citizen ID Card (Indonesia) / Passport">
                      <el-input v-model="form.idCard" />
                    </el-form-item>
                  </el-col>
                  <el-col :span="12">
                    <el-form-item label="Country">
                      <el-select v-model="form.country" clearable placeholder="Select Country">
                        <el-option
                          v-for="item in countryOptions"
                          :key="item"
                          :label="item"
                          :value="item"
                        />
                      </el-select>
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-form-item label="Address">
                  <el-input v-model="form.address" />
                </el-form-item>
                <el-row :gutter="20">
                  <el-col :span="8">
                    <el-form-item label="Place of Birth">
                      <el-input v-model="form.placeOfBirth" />
                    </el-form-item>
                  </el-col>
                  <el-col :span="8">
                    <el-form-item label="Date of Birth">
                      <el-date-picker
                        v-model="form.dateOfBirth"
                        type="date"
                        placeholder="Pick a date"
                        style="width: 100%;"
                      />
                    </el-form-item>
                  </el-col>
                  <el-col :span="8">
                    <el-form-item label="Gender">
                      <el-select v-model="form.gender" placeholder="Select Gender">
                        <el-option label="Male" value="male" />
                        <el-option label="Female" value="female" />
                      </el-select>
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-row :gutter="20">
                  <el-col :span="12">
                    <el-form-item label="Profile Picture">
                      <el-upload
                        class="avatar-uploader"
                        action="https://jsonplaceholder.typicode.com/posts/"
                        :show-file-list="false"
                        :on-success="handleAvatarSuccess"
                        :before-upload="beforeAvatarUpload"
                      >
                        <img v-if="imageUrl" :src="imageUrl" class="avatar">
                        <i v-else class="el-icon-plus avatar-uploader-icon" />
                      </el-upload>
                    </el-form-item>
                  </el-col>
                  <el-col :span="12">
                    <el-form-item label="ID Card / Passport Photo">
                      <el-upload
                        class="avatar-uploader"
                        action="https://jsonplaceholder.typicode.com/posts/"
                        :show-file-list="false"
                        :on-success="handleAvatarSuccess"
                        :before-upload="beforeAvatarUpload"
                      >
                        <img v-if="imageUrl" :src="imageUrl" class="avatar">
                        <i v-else class="el-icon-plus avatar-uploader-icon" />
                      </el-upload>
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-form-item label="Current Location">
                  <el-input v-model="form.currentLocation" />
                </el-form-item>
                <el-row :gutter="20">
                  <el-col :span="12">
                    <el-form-item label="Last Education">
                      <el-input v-model="form.lastEducation" />
                    </el-form-item>
                  </el-col>
                  <el-col :span="12">
                    <el-form-item label="Institution Name">
                      <el-input v-model="form.educationInstitutionName" />
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-row :gutter="20">
                  <el-col :span="12">
                    <el-form-item label="Current Activity">
                      <el-input v-model="form.currentActivity" />
                    </el-form-item>
                  </el-col>
                  <el-col :span="12">
                    <el-form-item label="Institution Name">
                      <el-input v-model="form.activityInstitutionName" />
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-form-item label="expertise">
                  <el-radio-group v-model="form.expertise">
                    <el-radio label="Tech (IT,Developer)" />
                    <el-radio label="Design" />
                    <el-radio label="Domain Experts (Art, Business, etc)" />
                  </el-radio-group>
                </el-form-item>
                <el-form-item label="Session Preference Tim">
                  <el-radio-group v-model="form.session">
                    <el-radio label="Session 1 (09.00-13.00)" />
                    <el-radio label="Session 2 (14.00-18.00" />
                    <el-radio label="Both Session" />
                  </el-radio-group>
                </el-form-item>
                <el-form-item label="Please tell us why you would want to join Apple Academy">
                  <el-input v-model="form.desc" type="textarea" />
                </el-form-item>
                <el-form-item label="How did you hear about our program?">
                  <el-checkbox-group v-model="form.type">
                    <el-checkbox label="Info Session" name="type" />
                    <el-checkbox label="Instagram" name="type" />
                    <el-checkbox label="Facebook" name="type" />
                    <el-checkbox label="Flyer" name="type" />
                    <el-checkbox label="Standing Banner" name="type" />
                    <el-checkbox label="Friends/Relatives" name="type" />
                  </el-checkbox-group>
                </el-form-item>
                <el-form-item>
                  <el-button type="primary" @click="onSubmit">Save</el-button>
                </el-form-item>
              </el-form>
            </div>
          </el-col>
        </el-row>
      </el-main>
    </el-container>
  </div>
</template>

<script>
// import DropdownMenu from "@/components/Share/DropdownMenu";

export default {
  name: 'PersonalInfo',
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

<style>
</style>
