
<script>
import moment from 'moment';
export default {
  name: "MyMixin",
  methods: {
    formatDate(val) {
      return moment(val).format("DD/MM/YYYY");
    },
    upperstring(val) {
      return val.toUpperCase();
    },
    lowerstring(val) {
      return val.toLowerCase();
    },
  },
};
</script>