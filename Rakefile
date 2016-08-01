require 'rake'
require 'fileutils'

desc "Set up dotfiles in standard locations"
task install: [:submodule_init, :submodules] do
  p
  p "===================================="
  p "Starting installation"
  p "===================================="
  p

  install_extras
  install_neovim
end

task :submodule_init do
end

task :submodules do
end

private

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
  p 'Would you like to install neovim? [y]es, [n]o'
  if STDIN.gets.chomp.downcase.include?('y')
    p "Adding Neovim repository (press enter)"
    run %{sudo add-apt-repository ppa:neovim-ppa/unstable}
    if $?.success?
      p "Installing Neovim"
      run %{sudo apt-get update}
      run %{sudo apt-get install -y neovim}
      p "Installing prerequisites for Python modules"
      run %{sudo apt-get install -y python-dev python-pip python3-dev python3-pip}
    end
  end
end

def run(cmd)
  p "[Running] #{cmd}"
  `#{cmd}` unless ENV['Debug']
end

def want_to_install?(item)
  p "Would you like to install configuration files for: #{item}? [y]es, [n]o"
  STDIN.gets.chomp.downcase.include?('y')
end
