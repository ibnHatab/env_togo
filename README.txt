0. Requirements:
   ipython
   bash-completion

1. Link or copy following files to the $HOME
	bin/             - some common scripts
	apps/		 - toolchain and emacs configs
	.bash_profile	 - toolchain defs
	.bashrc
	.bash_aliases
	.emacs		 - emacs config
	.erlang		 - erlang config
	.inputrc	 - ?
	.vimrc		 - vim config for trace reading :ic and :mounse

You can adapt this command to do the job for you:
for i in `find env_togo/ -maxdepth 1 | sed -e '1d' | grep -v .git`; do ln -sf $i; done

2. Get Erlang test tools

mkdir libs; cd libs
git clone gitolite@caprica:femto/femto_test
git config --global http.proxy $http_proxy
rebar get-deps
rebar compile

cd deps; git clone https://github.com/stesla/distel.git
cd distel; mkdir ebin; make erl

edit .erlang
