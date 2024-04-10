<template>
  <div class="container">
    <div class="profile-container">
      <div class="row align-items-center profile-header">
        <div class="col-md-2 mb-3 text-center">
          <img :src="user?.picture" alt="User's profile picture" class="rounded-circle img-fluid profile-picture" />
        </div>
        <div class="col-md-10">
          <h2 class="mb-0">{{ user?.name }}</h2>
          <p class="lead text-muted">{{ user?.email }}</p>
        </div>
      </div>

      <div class="row">
        <div class="col-md-12">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">Profile Details</h5>
              <highlightjs language="json" :code="JSON.stringify(user, null, 2)" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { useAuth0 } from '@auth0/auth0-vue';

export default {
  name: "ProfileView",
  setup() {
    const auth0 = useAuth0();

    return {
      user: auth0.user,
    }
  }
};
</script>

<style scoped>
.profile-container {
  margin-top: 20px;
}

.profile-header {
  border-bottom: 1px solid #dee2e6;
  padding-bottom: 20px;
}

.profile-picture {
  width: 120px;
  height: 120px;
}

.card {
  margin-top: 20px;
}
</style>
