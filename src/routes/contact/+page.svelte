<script>
import { onMount } from "svelte";
  import { getDatabase, ref, push } from "firebase/database";

  let formData = {
    name: "",
    email: "",
    subject: "", // Added subject field
    message: "",
  };

  const handleSubmit = async () => {
    const db = getDatabase();
    const contactsRef = ref(db, "contacts");

    // Push the form data to the "contacts" collection
    await push(contactsRef, formData);

    // Clear the form after submission
    formData = {
      name: "",
      email: "",
      subject: "",
      message: "",
    };

    // Alert after submission
    alert("Form submit successful!");

    console.log("Form submitted to Firebase Realtime Database!");
  };

  onMount(() => {
    document.title = "Contact";
  });
</script>

<!-- page title -->

<!-- end page title -->

<!-- section -->
<link rel="stylesheet" href="./css/bootstrap-reboot.min.css">
	<link rel="stylesheet" href="./css/bootstrap-grid.min.css">
	<link rel="stylesheet" href="./css/owl.carousel.min.css">
	<link rel="stylesheet" href="./css/magnific-popup.css">
	<link rel="stylesheet" href="./css/nouislider.min.css">
	<link rel="stylesheet" href="./css/jquery.mCustomScrollbar.min.css">
	<link rel="stylesheet" href="./css/paymentfont.min.css">
	<link rel="stylesheet" href="./css/main (1).css">
<section class="section">
  <div class="container">
    <div class="row">
      <div class="col-12 col-md-7 col-xl-8">
        <div class="row">
          <!-- section title -->
          <div class="col-12">
            <h2 class="section__title">Get in Touch</h2>
          </div>
          <!-- end section title -->

          <div class="col-12">
            <form on:submit={handleSubmit} class="form form--contacts">
              <input type="text" class="form__input" id="name" bind:value={formData.name} placeholder="Your Name">
              <input type="text" class="form__input" id="email" bind:value={formData.email} placeholder="Your Email">
              <input type="text" class="form__input" id="subject" bind:value={formData.subject} placeholder="Subject">
              <textarea name="text" class="form__textarea" id="message" rows="4" bind:value={formData.message} placeholder="Type your message..."></textarea>
              <button type="submit" class="form__btn">Send Message</button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
<!-- end section -->
