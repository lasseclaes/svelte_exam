<script>
  export let count = 0;

  let count2; // = count * 2;
  function increment() {
    count = count + 1;
  }
  //   $: let more = count * 2;

  function changeDocTitle() {
    document.title = count2 + document.title;
  }
  //updates state dependent on th count variable
  $: {
    if (count) {
      document.title = "smt " + `(` + count + `)`;
    }
    count2 = count * 2;
  }
</script>

<h1>Evaluering af Svelte og Sveltekit</h1>

<dl>
  <dt>
    Routing: Hvordan navigeres der imellem sider, kan der deep-linkes til sider?
    Kan man sende URL fragments, til fx. at aktivere et specifikt element eller
    tab på siden.
  </dt>
  <dd>
    <h3><a href="tests?smt=smt#here">tests?smt=smt#here</a>Yes? -</h3>
    <blockquote>
      <h4>Storing state in the URL</h4>
      <p>
        If you have state that should survive a reload and/or affect SSR, such
        as filters or sorting rules on a table, URL search parameters (like <code
          >?sort=price&amp;order=ascending</code
        >) are a good place to put them. You can put them in
        <code>&lt;a href="..."&gt;</code>
        or <code>&lt;form action="..."&gt;</code> attributes, or set them
        programmatically via <code>goto('?key=value')</code>. They can be
        accessed inside <code>load</code> functions via the <code>url</code>
        parameter, and inside components via
        <code>$page.url.searchParams</code>.
      </p>
    </blockquote>
    <a
      href="https://kit.svelte.dev/docs/state-management#storing-state-in-the-url"
      >https://kit.svelte.dev/docs/state-management#storing-state-in-the-url</a
    >
  </dd>
  <dt>
    State: Hvordan håndteres tilstand og UI opdatering i frameworket?
    <ol>
      <li>Hvor tungt er det at arbejde med?</li>
      <li>Er der meget boilerplate kode for at opnå det man vil?</li>
      <li>Hvordan persisterer man tilstand mellem 2 sider?</li>
      <li>Kan man bruge streams og fx redux store?</li>
    </ol>
  </dt>
  <dd>
    Godt. 1/2 automatisk state v. brug af variabel navn - "count": {count}.
    <button on:click={increment}>+1</button>

    <button on:click={changeDocTitle}>Change Doc title</button>
    Reactivity w/ $. - "count2" - og doc title, når "count " ændrer sig.
    <blockquote class="blockquote mx-3">
      <a
        href="https://svelte.dev/docs/svelte-components#script-2-assignments-are-reactive:~:text=Reactive%20statements%20run%20after%20other%20script%20code%20and%20before%20the%20component%20markup%20is%20rendered%2C%20whenever%20the%20values%20that%20they%20depend%20on%20have%20changed."
        >Reactive statements run after other script code and before the
        component markup is rendered, whenever the values that they depend on
        have changed.
      </a>
    </blockquote>
    Count2: {count2}
    <ol>
      <li>Tror det bliver ret let, når man lige har vænnet sig til det.</li>
      <li>Meget lidt v. standard-ting.</li>
      <li>Vha. stores</li>
    </ol>
  </dd>

  Tilgængelighed: Hvor god er opmærkningen og support for skærmlæsere med det
  HTML frameworket output’er? Hvis frameworket ikke selv har UI komponenter, så
  vil det være interessant med vurdering af UI biblioteker til frameworket.
  Arkitektur & Patterns: Er det nemt at skabe god struktur for ens kode med
  frameworket i større projekter? Er frameworket opinionated ift. om man bruger
  MVC, MVVM, Redux, eller andet pattern? (Se pattern eksempel) Form Validation:
  Er der indbygget form validation i frameworket? Hvor godt fungerer det? Fil
  operationer: Hvordan håndteres f.eks. en fil upload via formular i
  frameworket? Design fleksibilitet: Er der standard UI komponenter? Hvor nemt
  er det at ændre på udseendet og opførsel af standard UI komponenter?
  Authentication: Er der gode muligheder for at integrere med fx OpenID
  authentication i en app udviklet i frameworket? Community: Hvor aktivt et
  community er der omkring? Hvilket firma står bag og hvor langsigtet er deres
  support? Er det nemt at finde modne plugins til de funktionaliteter der ikke
  kommer med frameworket? Modenhed: Hvor modent er frameworket? Subjektiv
  vurdering ift. om det er i beta, hvor ofte der sker større API ændringer osv.
  Developer experience: Hvor nemt er frameworket at arbejde med? Er der gode
  værktøjer til debugging og profiling? Hvor hurtigt kan man hot-reload sine
  ændringer hvis man watcher koden? Bruger frameworket en pipeline fx. WebPack?
  Runtime konfiguration: Kan man bygge og derefter køre frontend med forskellige
  konfigurationer? Fx. hvilken backend den kører mod (nightly, beta, live).
</dl>

<style>
  dt,
  dl,
  dd {
    border: solid 1px black;
  }
</style>
