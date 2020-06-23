********
Webhooks
********

Incoming Webhooks and Automation

================================

The primary method that Read the Docs uses to detect changes to your documentation and versions is through the use of \*webhooks*. Webhooks
are configured with your repository provider, such as GitHub, Bitbucket or GitLab, and with each change to your repository, Read the Docs is notified. When
we receive a webhook notification, we determine if the change is related to
an active version for your project, and if it is, a build is triggered for
that version.

Webhook Integrations
====================

You'll find a list of configured webhook integrations on your project's
:guilabel:`Admin\`dashboard, under :guilabel:`Integrations`. You can select any of these
integrations to see the \*integration detail page*. This page has additional
configuration details and a list of HTTP exchanges that have taken place for the
integration.

You need this information for the URL, webhook, or Payload URL needed by
the repository provider such as GitHub, GitLab, or Bitbucket.

.. \_webhook-creation:

Webhook Creation
================

If you have :doc:`connected your Read the Docs account </connected-accounts>\` to GitHub, Bitbucket, or GitLab,

\**a webhook will be set up automatically for your repository**.
However, if your project was not imported through a connected account, you may need to manually configure a webhook for your project.

To manually set up a webhook, go to :guilabel:`Admin\` >:guilabel:`Integrations\` > :guilabel:`Add integration\`dashboard page and select the integration type you'd like to add.

After you have added the integration, you'll see a link to information about the integration.

As an example, the URL pattern looks like this:
\*https://readthedocs.org/api/v2/webhook/<project-name>/<id>/*.

Use this URL when setting up a new webhook with your provider -- these steps vary depending on the provider.

.. note::

If your account is connected to the provider, we'll try to setup the webhook automatically. If something fails, you can still setup the webhook manually.

.. \_webhook-integration-github:

GitHub

~~~~~~

\* Go to the :guilabel:`Settings\` page for your project

\* Click :guilabel:`Webhooks\` > :guilabel:`Add webhook\`

\* For \**Payload URL**, use the URL of the integration on Read the
Docs,

found on the project's :guilabel:`Admin\` > :guilabel:`Integrations\`
page.

You may need to prepend \*https://\* to the URL.

\* For \**Content type**, both \*application/json\* and

\*application/x-www-form-urlencoded\* work

\* Leave the \**Secrets*\* field blank

\* Select \**Let me select individual events**,

and mark \**Branch or tag creation**, \**Branch or tag deletion*\* and
\**Pushes*\* events

\* Ensure \**Active*\* is enabled; it is by default

\* Finish by clicking \**Add webhook**. You may be prompted to enter
your GitHub password to confirm your action.

You can verify if the webhook is working at the bottom of the GitHub page under \**Recent Deliveries**.

If you see a Response 200, then the webhook is correctly configured. For a 403 error, it's likely that the Payload URL is incorrect.

GitHub will emit an initial HTTP request (`X-GitHub-Event: ping`) upon creating the webhook and you may notice that the Read the Docs responds with \`{"detail":"Unhandled webhook event"}\` – this is normal and expected.

Push changes to your repository and webhooks will work from this point.

.. note:: The webhook token, intended for the GitHub \**Secret*\* field,
is not yet implemented.