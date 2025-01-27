---
html_meta:
  "description": "Learn How to customize the Footer of the page"
  "property=og:description": "Learn How to customize the Footer of the page"
  "property=og:title": "Footer customization"
  "keywords": "Plone, Volto, Training, Theme, Footer"
---

(voltohandson-footer-label)=

# Footer

We customize the footer using component shadowing, by copying the original Volto `Footer` component from the `omelette` folder (`omelette/src/components/theme/Footer/Footer.jsx`) into the `customizations/components/theme/Footer/Footer.jsx` file.

Since we need the Logo component in the Footer, we import it from Volto as we did in the Header:

```jsx
import { Logo } from "@plone/volto/components";
```

Then, we replace the `Footer` component content to match the one from `plone.org`.

```jsx
<Segment role="contentinfo" vertical padded inverted color="black">
  <Container>
    <Segment basic inverted color="black" className="discreet footer">
      <div className="footer-inner">
        <Logo />
        <List horizontal inverted>
          {/* wrap in div for a11y reasons: listitem role cannot be on the <a> element directly */}
          <div role="listitem" className="item">
            <Link className="item" to="/sitemap">
              <FormattedMessage id="Site Map" defaultMessage="Site Map" />
            </Link>
          </div>
          <div role="listitem" className="item">
            <Link className="item" to="/accesibility-info">
              <FormattedMessage
                id="Accessibility"
                defaultMessage="Accessibility"
              />
            </Link>
          </div>
          <div role="listitem" className="item">
            <Link className="item" to="/contact-form">
              <FormattedMessage id="Contact" defaultMessage="Contact" />
            </Link>
          </div>
          <div role="listitem" className="item">
            <a className="item" href="https://plone.org">
              <FormattedMessage
                id="Powered by Plone & Python"
                defaultMessage="Powered by Plone & Python"
              />
            </a>
          </div>
        </List>
      </div>

      <p>
        The Plone® CMS/WCM is © 2000–2019 the Plone Foundation and friends.
        <br />
        Plone® and the Plone logo are registered trademarks of the Plone
        Foundation.
        <br /> You’re looking good today!
      </p>
    </Segment>
  </Container>
</Segment>
```

and add this styling to the `custom.overrides` file:

```less
.ui.inverted.black.segment {
  background-color: #191919 !important;

  .footer {
    .ui.image {
      height: 32px;
      margin-right: 50px;
      color: @white;
    }

    .footer-inner {
      display: flex;
      align-items: center;
      margin-bottom: 20px;

      .ui.horizontal.list a {
        text-decoration: none;
      }
    }
  }
}
```
