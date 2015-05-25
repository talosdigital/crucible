Talos Digital - Docker-Crucible
===============

A simple container in order to start using [Atlassian Crucible](https://www.atlassian.com/software/crucible/overview)

Based on the [Dockerfile/Jahroots/docker-crucible](https://github.com/Jahroots/docker-crucible) container, extended for our internal usage in the company.

This container exposes 2 ports:

	* 22   : for the ssh service (avoid to expose this service)
	
	* 8060 : for the crucible server

### Fig config (fig.yml)
	opt:
	  image: talosdigital/crucible
	  volumes:
	    - /opt
	  command: true

	db:
	  image: talosdigital/crucible
	  volumes_from:
	    - opt
	  ports:
	    - "8060:8060"

### Usage
	fig up
	
Recommended security crucible configuration:

	* Admin > Permission Schemes - Default Project - remove View for anonymous

	* Admin > Authentication

		* Turn Off: Global Anonymous Access
		* Turn Off: Crucible Anonymous Access
		* Turn Off: Public Signup
