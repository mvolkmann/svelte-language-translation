<script>
  import {onMount} from 'svelte';
  import {
    getSupportedLanguages,
    i18n as originalI18n,
    setLanguage
  } from 'web-translate';
  import {i18n} from './stores';

  let languageCode;
  let languages;
  let languageNames = [];

  onMount(async () => {
    // Get the languages listed in public/languages.json.
    languages = await getSupportedLanguages();
    languageNames = Object.keys(languages);
  });

  async function handleChange(event) {
    languageCode = event.target.value;
    await setLanguage(languageCode);
    // Doing this triggers interpolations
    // that use $i18n to re-render.
    i18n.set(originalI18n);
  }
</script>

<select on:change={handleChange} value={languageCode}>
  {#each languageNames as name}
    <option value={languages[name]}>{name}</option>
  {/each}
</select>
