<template>
  <header>
    <div class="header-top-bar">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-6">
            <ul class="top-bar-info list-inline-item pl-0 mb-0">
              <li class="list-inline-item">
                <a href="mailto:support@gmail.com"
                  ><i class="icofont-support-faq mr-2"></i
                  >edgar.dimas.ir@gmail.com</a
                >
              </li>
              <li class="list-inline-item">
                <i class="icofont-location-pin mr-2"></i>Address Ta-134/A, New
                York, USA
              </li>
            </ul>
          </div>
          <div class="col-lg-6">
            <div class="text-lg-right top-right-bar mt-2 mt-lg-0">
              <a href="tel:+23-345-67890">
                <span>Call Now : </span>
                <span class="h4">823-4565-13456</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <nav class="navbar navbar-expand-lg navigation" id="navbar">
      <div class="container">
        <a class="navbar-brand" href="index.html">
          <img
            src="../images/logo.png"
            alt=""
            class="img-fluid"
            style="height: 150px"
          />
        </a>

        <button
          class="navbar-toggler collapsed"
          type="button"
          data-toggle="collapse"
          data-target="#navbarmain"
          aria-controls="navbarmain"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="icofont-navigation-menu"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarmain">
          <ul class="navbar-nav ml-auto">
            <li class="nav-item active">
              <a @click.prevent="doHome()" class="nav-link" href="index.html"
                >Home</a
              >
            </li>
            <li class="nav-item">
              <a @click.prevent="doLogin()" class="nav-link" href="about.html"
                >Login</a
              >
            </li>
            <li class="nav-item">
              <a
                @click.prevent="doLogout()"
                class="nav-link"
                href="service.html"
                >Logout</a
              >
            </li>
            <li class="nav-item">
              <a
                @click.prevent="doAppoint()"
                class="nav-link"
                href="service.html"
                >Appoint Doctors</a
              >
            </li>
            <li class="nav-item">
              <a
                @click.prevent="doMyAppoint()"
                class="nav-link"
                href="service.html"
                >MyAppointments</a
              >
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
import { mapActions } from "pinia";
import { useCounterStore } from "../stores/counter";
import Swal from "sweetalert2";
mapActions;
export default {
  props: ["element"],
  methods: {
    ...mapActions(useCounterStore, ["appointStore", "getDoctors2"]),
    doMyAppoint() {
      this.$router.push("/myappointments");
    },
    doAppoint() {
      this.$router.push("/appoint");
    },
    doLogin() {
      this.$router.push("/login");
    },
    doLogout() {
      localStorage.clear();
      this.$router.push("/");
      Swal.fire({
        title: "Logged out notice",
        text: "You have been logged out",
        icon: "info",
        confirmButtonText: "Ok",
      });
    },
    doHome() {
      this.$router.push("/");
    },
  },
};
</script>
