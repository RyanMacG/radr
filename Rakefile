require 'rake'
require 'fileutils'

desc "Set up dotfiles in standard locations"
task install: [:submodule_init, :submodules] do
  p
  p "===================================="
  p "Starting installation"
  p "===================================="
  p

  install_extras if RUBY_PLATFORM.downcase.include?('linux')
end

task :submodule_init do
end

task :submodules do
end

# All the install methods happen down here

def install_extras
  p
  p "===================================="
  p "Installing a bevvy of useful utilities"
  p "===================================="
  p
  run %{sudo apt upgrade -y}
  run %{sudo apt install -y zsh ctags git tmux xclip silversearcher-ag guake}
end

def install_neovim
end

private

def run(cmd)
  puts "[Running] #{cmd}"
  `#{cmd}` unless ENV['Debug']
end
