---
title: Opencast 7.0 has been released
date: 2019-06-14
description: This new major release includes several new features and improvements.
category: release
tags: [release]
---

# Opencast 7: Release Notes

## New Features

- Overhaul of the permission management with the newly added possibility to define how access control lists are evaluated and how series permission changes are populated to episodes. For more details take a look at the access control configuration guide.
- Update Elasticsearch and make it possible to run Elasticsearch as an external service.
- Per-Tenant Capture Agent Users
- Asset manager snaphots clean-up to remove older snapshots for a given media package. In some cases, this can drastically reduce Opencast's storage consumption. This feature is implemented as an option for the asset-delete workflow operation handler.
- Allow the workflow to select the audio track for composite video
- Add multi-tenant support for all list providers
- Make waveform size configurable
- Create a generic user interface configuration service
- In the events table add a link to the series details
- Add internationalization support for series LTI tools
- Display creator of workflow
- Allow the ingest service to make authenticated requests to other servers
- Some modules are now plugins. These are not started by default to reduce the amount of code running unnecessarily. They can easily be enabled in etc/org.apache.karaf.features.cfg. Modified modules are:
- Moodle user directory
- Sakai user directory

## Improvements

A non-comprehensive list of improvements:

- Improved performance when scheduling new events or checking for conflicts (reducing the time for adding multiple schedules by up to 90%).


## Configuration changes
- `etc/org.opencastproject.scheduler.impl.SchedulerServiceImpl.cfg` has a new option `maintenance` which temporarily disables the scheduler if set to true.
- ``KARAF_NOROOT` is now set to `true` by default, preventing Opencast to be started as root user unless the configuration is changed.
- The default configuration for the Paella player has been moved to `etc/ui-config/mh_default_org/paella/config.json`
- By default, metadata catalogs and attachments sent by capture agents are discarded since this data is usually controlled by Opencast and the routing through capture agents which existed for historical reasons was just an additional source for errors. If you rely on the old behavior, it can be configured in `etc/org.opencastproject.ingest.impl.IngestServiceImpl.cfg`.
- By default, the Paella player now respects all tracks published to engage instead of having a hard-coded filter for tracks with the sub-flavor `delivery` only.
- The structure of the configuration files concerning URL signing has changed. See the stream security configuration for more details.


## API changes

Due to MH-13397:

- Modified GET /recordings/{id}/technical.json: Removed field optOut
- Removed GET /recordings/{id}/optOut
- Removed GET /recordings/{id}/reviewStatus
- Removed PUT /recordings/{id}/reviewStatus
- Modified POST /recordings: Removed form parameter optOut
- Modified POST /recordings/multiple: Removed form parameter optOut
- Modified PUT /recordings/{id}: Removed form parameters optOut and updateOptOut
- Removed GET /series/{id}/optOut

Due to MH-13446:

- Removed GET /acl-manager/transitions.json
- Removed GET /acl-manager/transitionsfor.json
- Removed POST /acl-manager/episode/{id}
- Removed POST /acl-manager/series/{id}
- Modified POST /acl-manager/apply/episode/{id}: Removed form parameters workflowDefinitionId and workflowParams
- Modified POST /acl-manager/apply/series/{id}: Removed form parameters workflowDefinitionId and workflowParams
- Removed DELETE /acl-manager/episode/{transitionId}
- Removed DELETE /acl-manager/series/{transitionId}
- Removed PUT /acl-manager/episode/{transitionId}
- Removed PUT /acl-manager/series/{transitionId}

The Opencast codebase is located on [GitHub](https://github.com/opencast/opencast).

A full list of changes can be found in the [official release notes](https://docs.opencast.org/r/7.x/admin/releasenotes/).

Visit the [installation guide](https://docs.opencast.org/r/7.x/admin/installation/) for more information on how to get Opencast 7.
