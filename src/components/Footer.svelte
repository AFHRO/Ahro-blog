<script>
  import Container from "./Container.svelte";
  import Space from "./Space.svelte";
  import logo from "$lib/Logo With Text Under.svg";
  import footerLinks from "src/utils/footerLinks";
</script>

<footer class="footer">
  <Container class="footer__container">
    <div class="sections-list">
      <img src={logo} alt="AHRO" width="100" class="footer__logo" />

      {#each footerLinks as linkObject}
        <section class="footer__section">
          <h5>{linkObject.title}</h5>
          <Space direction="column">
            {#each linkObject.links as link}
              <a href={link.url} aria-label={`Footer link to ${link.title}`}
                >{@html link.title}</a
              >
            {/each}
          </Space>
        </section>
      {/each}
    </div>
    <div class="footer__bottom">
      <div>
        <span class="footer__copyright"
          >{@html "&copy"} {new Date().getFullYear()} AHRO</span
        >
        <a href="/" aria-label="visit privacy policy page">Privacy Policy</a>
        <a href="/" aria-label="Learn about our terms">Terms and Conditions</a>
        <a href="/" aria-label="Check cookie ploicy">Cookie Policy</a>
      </div>
      <div>
        <a href="/" aria-label="Check our facbook page"> Facebook </a>
        <a href="/"> Twitter </a>
        <a href="/"> Instagram </a>
      </div>
    </div>
  </Container>
</footer>

<style lang="scss">
  :global(.footer__container) {
    background-color: var(--primary-background-color);
    padding: 60px 0;
  }

  .footer {
    margin-top: 10rem;
    padding-top: 4rem;
    padding-bottom: 4rem;

    &__logo {
      align-self: flex-start;

      @media screen and (min-width: 768px) {
        width: clamp(10rem, 10vw, 20rem);
      }
    }
    .sections-list {
      display: flex;
      width: 100%;
      gap: 4rem;
      flex-direction: column;
      border-bottom: 1px solid var(--input-border-grey);
      padding-bottom: 4rem;
      @media screen and (min-width: 768px) {
        flex-direction: row;
        justify-content: space-between;
        gap: clamp(5rem, 3vw, 10rem);
      }
      margin: 0 auto;
    }
    &__section {
      h5 {
        margin-bottom: 2rem;
        color: var(--text-grey);
        text-transform: uppercase;
      }
      a {
        width: 100%;
        &:hover {
          color: var(--primary-color);
          text-decoration: underline;
        }
      }
    }

    &__bottom {
      display: flex;
      justify-content: space-between;
      margin-top: 4rem;
      flex-direction: column-reverse;
      gap: 3rem;

      @media screen and (min-width: 1024px) {
        flex-direction: row;
        gap: 3rem;
      }

      a {
        &:hover {
          color: var(--primary-color);
        }
      }

      & > * {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;
        gap: 3rem;
      }
      @media screen and (min-width: 768px) {
        & > * {
          flex-direction: row;
        }
      }
    }
    &__copyright {
      color: var(--text-grey);
      font-size: 1.8rem;
    }
  }
</style>
