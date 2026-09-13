# Argo Alert — production dashboard

Published at https://gotoopraveen-ops.github.io/argo-alert-prod-dashboard/

| | |
|---|---|
| Firmware | 5.0.0, `rf_monitor_hive_user_credential_production_v1/` |
| App | apt-alrt-asist 5.0.0 or later |
| Remote API level | 6 |

## One key per customer

A customer signs in with a single line:

```
stmarys:<the password you set in the console>
```

That is their broker account, written as one line. In HiveMQ those are two
separate fields; the colon is only how the two are joined together for the
customer to type once.

The part before the colon is also their topic prefix, so one line carries both
who they are and where their panels live.

**Never use a password written in this file.** It is a public repository.

Nothing about the key is checked here. The broker either accepts it or does
not, which is the only opinion that counts. A key that works reaches exactly
one customer's panels, because that is all its permissions allow, whatever this
page does. **That is the difference from every earlier version**, where the page
decided what to show and a shared credential could read everything.

The optional prefix field exists for systems set up before the keys were
issued, where the account name and the prefix are not the same word. New
customers leave it empty.

## Adding a customer

Two credentials in the HiveMQ console, both restricted to that customer's
prefix. One goes into their panels when the installer sets them up, the other
is the key you hand the customer.

Nothing is rebuilt. No repository is pushed. No app is redistributed. Selling
to a new customer does not touch the code, which is the whole point.

Two rather than one so that a lost phone costs a credential change and not a
drive to every panel: rotate the staff key, and the panels never notice.

## What is not here any more

Per panel pairing, signed commands, and the customer table that used to be
compiled into the page and the app. All three existed to work around one broker
credential being shared by everybody. With a credential per customer the broker
does that job properly, and none of them earn their place.

## Still open

The broker is a free tier, capped at a hundred connections. Twenty five panels
and their phones sit comfortably inside it; fifty would not.
