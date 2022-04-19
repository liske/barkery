# barkery - digital signage based on WebKit2

This is project provides a *WebKit2* bases kiosk browser to be used for digital signage. It has a *MQTT* interface for remote management.

It is implemented in *Python3* and uses *Glib GObject Introspection* for the *Gtk3* and *Webkit2* stuff. It will run on *Raspberry Pi* using read only rootfs.

## Prerequisits

- *Python3*
- *Glib GObject Introspection*
  - *Gtk3*
  - *WebKit2*
- *Paho MQTT*

## History

This is the successor of *barkery* reimplemented in *Python3*. *Barkery* has used the same approach but was implemented in *Perl5* and never published. *Barkery* was used on *Raspbian Lite* with read-only root.

Switching to *Alpine Linux* using *barkery* was not possible since there are missing some *Perl5* bindings. Since *Gtk* and *WebKit2* is integrated via *Glib GObject Introspection* it was more easy to port the project to *Python3* than I did expect.

For example the old *Perl5* code:

```perl
my $screen = Gdk3::Screen::get_default();

my $window = Gtk3::Window->new('toplevel');
$window->set_wmclass('barkery-terminal', 'Barkery Terminal');
$window->set_role('browser');
$window->set_icon_name('text-html');
$window->set_default_size($screen->get_width, $screen->get_height);

my $scrolls = Gtk3::ScrolledWindow->new;
my $view = WebKit::WebView->new;
$scrolls->add($view);

$window->add($scrolls);
$window->show_all;
$window->present;

# ...

# main loop
Gtk3::main();
```

has been transcribed to:

```python
screen = Gdk.Screen.get_default()
window = Gtk.Window.new(Gtk.WindowType.TOPLEVEL)
window.set_role('browser')
window.set_icon_name('text-html')
window.set_default_size(screen.get_width(), screen.get_height())

scrolls = Gtk.ScrolledWindow.new()
view = WebKit2.WebView.new()
scrolls.add(view)

window.add(scrolls)
window.show_all()
window.present()

# ...

# main loop
Gtk.main()
```
