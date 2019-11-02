<script>
  import english from './en.json';
  import spanish from './es.json';
  import french from './fr.json';

  export let language = 'en';

  let translationMap = {
    en: english,
    es: spanish,
    fr: french
  };
  
  $: translations = translationMap[language];
</script>

<select bind:value={language}>
  <option value="en">English</option>
  <option value="fr">French</option>
  <option value="es">Spanish</option>
</select>

<h1>{translations.hello}</h1>
<h1>{translations.goodbye}</h1>
