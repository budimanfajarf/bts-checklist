<template>
  <div>
		<h1>BTS.id - CheckList</h1>
		<ul>
			<li v-for="(theCheck) in checklist" :key="theCheck.id">
				<input
					type="checkbox"
					:name="'check'+theCheck.id"
					:id="'check'+theCheck.id"
					:value="theCheck.id"
					:checked="theCheck.checklistCompletionStatus == true ? 'checked' : ''"
				>
				<label :for="'check'+theCheck.id">
					{{ theCheck.id }} - {{ theCheck.name }} - {{ theCheck.checklistCompletionStatus }}
				</label>

				<ul v-if="theCheck.items && theCheck.items.length > 0">
					<li v-for="(theItem) in theCheck.items" :key="theItem.id">
						<input
							type="checkbox"
							:name="'item'+theItem.id"
							:id="'item'+theItem.id"
							:value="theItem.id"
							:checked="theItem.itemCompletionStatus == true ? 'checked' : ''"
						>
						<label :for="'item'+theItem.id">
							{{ theItem.id }} - {{ theItem.name }} - {{ theItem.itemCompletionStatus}}
						</label>
					</li>
				</ul>
			</li>
		</ul>
	</div>
</template>

<script>
import axios from "axios";

export default {
  name: "CheckList",
  data() {
    return {
      api: {
        baseUrl: "http://18.139.50.74:8080",
        authorization: {
          headers: {
            Authorization:
              "Bearer eyJhbGciOiJIUzUxMiJ9.eyJyb2xlcyI6W119.i2OVQdxr08dmIqwP7cWOJk5Ye4fySFUqofl-w6FKbm4EwXTStfm0u-sGhDvDVUqNG8Cc7STtUJlawVAP057Jlg",
          },
        },
			},
			checklist: []
    };
  },
  mounted() {
    this.getChecklist();
  },
  methods: {
    getChecklist() {
      axios
        .get(this.api.baseUrl+'/checklist', this.api.authorization)
        .then((response) => {
					// console.log(response);
					this.checklist = response.data.data;
					console.log(this.checklist);
        })
        .catch((error) => {
          if (error) {
            alert(error);
          }
        })
        .finally(() => {});
    },
  },
};
</script>
