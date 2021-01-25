<template>
  <h1>email test</h1>
</template>

<script>
import axios from "axios";

export default {
  mounted () {
    axios({
      method: 'post',
      url: 'https://api.emailjs.com/api/v1.0/email/send/',
      data: {
        service_id: 'service_n1nlx9r',
        template_id: 'template_e5mh7zg',
        user_id: 'user_s0M53u6qxQpT90KoWRp78',
        template_params: {
          'subject': 'test subject',
          'message': '<p>test message</p>',
          'to': 'kim@4siteusa.com',
          'from_name': 'from test name',
        }
      }
    })
  }
}
</script>
