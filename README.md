Elgg on OpenShift
=========================
Elgg is an award-winning open source social networking engine that provides a robust framework on which to build all kinds of social environments, from a campus wide social network for your university, school or college or an internal collaborative platform for your organization through to a brand-building communications tool for your company and its clients.

More information can be found on the official elgg website at http://elgg.org

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a PHP application

	rhc app create -a elgg -t php-5.3

Add mysql support to your application
    
	rhc app cartridge add -a elgg -c mysql-5.1
Make a note of the username, password, and host name as you will need to use these to complete the Piwik installation on OpenShift

Add this upstream elgg quickstart repo

	cd elgg 
	git remote add upstream -m master git://github.com/gshipley/elgg-openshift-quickstart.git
	git pull -s recursive -X theirs upstream master

Then push the repo upstream to OpenShift

	git push

That's it for the code, you can now install your application at:

	http://elgg-$yournamespace.rhcloud.com

When the installation asks you for your data directory, use the same information as for the Elgg installation which should look something like this:

	/var/lib/libra/A BUNCH OF RANDOM CHARACTERS/elgg/runtime/repo/php/

Remove the /runtime/repo/php and add data so it looks like:

	/var/lib/libra/A BUNCH OF RANDOM CHARACTERS/elgg/data




