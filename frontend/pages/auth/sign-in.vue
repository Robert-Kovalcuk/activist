<template>
  <div class="px-4 sm:px-6 md:px-8 xl:px-24 2xl:px-36">
    <form class="space-y-4">
      <div class="col">
        <FormTextField
          @update:model-value="userNameValue = $event"
          :placeholder="$t('pages.auth.sign-in.index.enter-user-name')"
          :model-value="userNameValue"
        />
      </div>
      <div>
        <FormTextField
          @update:model-value="passwordValue = $event"
          :placeholder="$t('components._global.enter-password')"
          :is-icon-visible="true"
          input-type="password"
          :model-value="passwordValue"
          :icons="['bi:eye-fill']"
        />
      </div>
      <IndicatorPasswordStrength :password-value="passwordValue" />
      <div class="flex flex-col space-y-3">
        <FriendlyCaptcha />
        <BtnAction
          @click="signIn"
          class="flex max-h-[48px] w-[116px] items-center justify-center truncate md:max-h-[40px] md:w-[96px]"
          :label="$t('_global.sign-in')"
          :cta="true"
          fontSize="lg"
          :ariaLabel="$t('components.btn-route-internal.sign-in-aria-label')"
        />
      </div>
      <div class="flex pt-4 md:justify-center md:pt-6 lg:pt-8">
        <h6>{{ $t("pages.auth.sign-in.index.no-account") }}</h6>
        <NuxtLink
          :to="localePath('/auth/sign-up')"
          class="link-text ml-2 font-extrabold"
          >{{ $t("_global.sign-up") }}</NuxtLink
        >
      </div>
    </form>
  </div>
</template>

<script setup lang="ts">
import useRouteToName from "~/composables/useRouteToName";

definePageMeta({
  layout: "auth",
});

const emit = defineEmits(["routeToName"]);
useRouteToName(emit);

const localePath = useLocalePath();

definePageMeta({
  layout: "auth",
});

const userNameValue = ref("");
const passwordValue = ref("");

const signIn = () => {
  //
};
</script>
