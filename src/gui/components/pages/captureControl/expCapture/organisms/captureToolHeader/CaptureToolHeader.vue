<!--
 Copyright 2022 NTT Corporation.

 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
-->

<template>
  <v-layout
  justify-space-between
  align-space-between
  row
  @keydown="cancelKeydown"
>
  <div>
    <v-layout>
      <url-text-field />
      <test-result-name-text-field />
      <v-btn
        color="primary"
        @click="submitForm"
      >
        Submit
      </v-btn>
    </v-layout>
  </div>
</v-layout>

    <div>
      <v-layout>
        <record-button />
        <pause-button />
        <clear-history-button />
       
      </v-layout>
    </div>
    <div>
  <v-layout>
    <load-history-button />
    <menu-button />
    <v-spacer />
    <v-icon @click="openSettings">settings</v-icon>
  </v-layout>
</div>
<v-menu
  top
  offset-y
  origin="center center"
  transition="scale-transition"
  :close-on-content-click="false"
>
  <template v-slot:activator="{ on, attrs }">
    <v-btn icon flat large v-bind="attrs" v-on="on">
      <v-icon>menu</v-icon>
    </v-btn>
  </template>
  

  <v-list>
    <v-list-item>
      <v-list-item-title>
        <v-flex shrink pa-1 pl-3>
          <locale-select-box />
        </v-flex>
      </v-list-item-title>
    </v-list-item>
    <v-list-item>
      <v-list-item-title>
        <v-flex shrink pa-1 pl-3>
          <remote-access-field color="inherit" />
        </v-flex>
      </v-list-item-title>
    </v-list-item>
    <v-list-item>
      <v-list-item-title>
        <v-flex shrink pa-1 pl-3>
          <v-switch label="Dark Mode" v-model="darkMode" />
        </v-flex>
      </v-list-item-title>
    </v-list-item>
  </v-list>
</v-menu>


</template>

<script lang="ts">
import RemoteAccessField from "@/components/pages/common/organisms/RemoteAccessField.vue";
import { Component, Vue } from "vue-property-decorator";
import ClearHistoryButton from "./ClearHistoryButton.vue";
import GenerateTestScriptButton from "./GenerateTestScriptButton.vue";
import LoadHistoryButton from "./LoadHistoryButton.vue";
import LocaleSelectBox from "./LocaleSelectBox.vue";
import PauseButton from "./PauseButton.vue";
import RecordButton from "./RecordButton.vue";
import TestResultNameTextField from "./TestResultNameTextField.vue";
import URLTextField from "./URLTextField.vue";
import MenuButton from "./MenuButton.vue";

@Component({
  components: {
    "url-text-field": URLTextField,
    "test-result-name-text-field": TestResultNameTextField,
    "record-button": RecordButton,
    "pause-button": PauseButton,
    "clear-history-button": ClearHistoryButton,
    "load-history-button": LoadHistoryButton,
    "generate-test-script-button": GenerateTestScriptButton,

    "locale-select-box": LocaleSelectBox,
    "remote-access-field": RemoteAccessField,
    "menu-button": MenuButton,
  },
})
export default class CaptureToolHeader extends Vue {
submitForm: any;
openSettings: any;
darkMode: any;
  private cancelKeydown(event: Event) {
    event.stopPropagation();
  }
}
</script>
