<script>
  import {i18n} from './stores';
  import LanguageSelect from './LanguageSelect.svelte';
</script>

<LanguageSelect />

<h1>{$i18n('hello')}</h1>
<h1>{$i18n('goodbye')}</h1>
