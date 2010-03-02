__Is anyone using Mojo for production?__

Yes, despite of Mojo's "under heavy development" state.

__What was the magic env variable to get more dispatcher debugging?__

There is a lot dispatching logging in development mode. Make sure to check your log file and state.

__Can a Mojo app be a mix of ::Lite and normal Mojolicious ?__

Yes, it can. You can start writing you app as a ::Lite application and step by step grow to a normal one. One thing to remember is that there can be only one entry point, but you can share templates and controllers.

__Does Mojolicious have a concept of form handling?__

No. Mojolicious is just a framework that doesn't get in your way. There are many form handling modules on CPAN.

__What does 'shagadelic' mean?__

http://www.urbandictionary.com/define.php?term=shagadelic

__But doesn't 'shagadelic' mean fuckable?__

Not really.

__Didn't someone have a vim syntax for epl?__

http://github.com/korshak/Vim-Mojo-Data-syntax

__Okay, where the actual manual?__

It is being written.

__Does Mojo have forward and detach functions like cat?__

No it doesn't.

__Can Mojo be ran as a CGI script? For shared hosting services?__

Sure.

__Anything noteworthy built using Mojo yet?__

Bootylicious blog engine
Contenticious CMS
Pastelicious paste service

__Does Mojo natively support sessions?__

Yes. Or you can use MojoX::Session instead.

__How can I help out or otherwise support this project?__

Just use it, report bugs and ask for features. We are always glad to help.

__Hello there. Does Mojo have ORM?__

No. But there are a lot of ORMs on CPAN.

__Do you really only depend on version zero of everything?__

Besides Perl 5.8.1.

__Does Mojo have "models" like Catalyst?__

No. Why use additional abstract layer when you can just 'use' your model in controller?

__Mojo does its own accessor stuff?__

Yes. Mojo::Base provides basic accessors.

__Has sri released recently?__

Release cycle is a subject to change.

__What am I doing wrong?__

Could be anything. If you think that something is wrong, write a test app and drop a line to the mailing list or IRC channel.

__Does anybody know how the animated gifs on the Mojolicious webpage were created?__

Snapz pro x, Quicktime and ImageMagick. That's a long way: capture movie, split movie into frames, join frames into gif.

__Does Mojo do any gzip/deflating?__

No.

__Are there bridge examples anywhere ?__

Here are some: http://mojolicious.org/

__Does Mojo distinguish between /url/ and /url ?__

Mojo does, routes -- not so much.

__How is your documentation process going?__

__Is there some Mojolicious command line tool?__

Yes. For generating applications. It's called 'mojolicious'.

__Where do you want bug reports?__

IRC (#mojo at irc.perl.org) or mailing list (http://groups.google.com/group/mojolicious).

__Mojo's license is AL, any reason you didn't go with same as Perl? (GPL or AL)__

    <@sri> i've been reading the licenses recently and i liked AL most

__I just switched to Mojo, I am redoing my personal website. Should I use Mojo or Mojolicious::Lite for this task?__

Mojolicious::Lite is enough for a personal website.

__What exactly does the "shagadelic" method do?__

Calls Mojolicious::Lite->start that calls Mojolicious->start that calls Mojolicious::Command->start.

__Am I doing something wrong, perldoc Mojo::Manual::Mojolicious doesn't contain anything useful?__

__Where is the documentation for mojo?__

__How can I set content-type in Mojolicious::Lite app?__

    $self->res->headers->content_type()

__Anyone here use git tags?__

__want to port mojo to perl6?__

__Does "unsupported" mean "don't use" or just "swim at your own risk"?__

Both :)

__A simple Mojo wiki anyone?__

Feel free to take "wikilicious" as a name.

__where is all this great documentation i've been hearing about?__

__Stylish pdf mojo cheatsheet?__

__Does mojo have an email module?__

No. But CPAN does.

__Is anyone awake here?__

If nobody answers your question at the IRC channel, don't worry, it will be answered when somebody wakes up.

__How to run Mojo as a CGI script, using a browser?__

Use shagadelic('cgi') or MyApp->start('cgi') in your Mojolicious script.

__Can't you use host => qr// with route?__

Take a look at routes conditions.

__How would you redirect in Mojo?__

    $self->return_to('http://my-new-url.com');

__Does Mojo have a built-in way to add accessors to your app?__

    use base 'Mojo::Base';

__Where do I define the db connection?__

In sub process.

__Does Mojolicious reload itself after file changing?__

Set MOJO_RELOAD=1 or use --reload option.

__How to include other files inside epl?__

    $self->render_partial

__Is it a coincidence that there is a Catalyst wiki called mojomojo?__

__Do you plan use Moose in Mojo?__

Unlikely. Slow startup, countless prereqs and some being XS.

__Does Mojo::Loader catch syntax errors?__

Of course it does.

__Where can I see an example of Mojolicious + MojoX::Session?__

Look at MojoX::Session's distribution examples/ directory.

__Is there an easy way to change the templates base dir for Mojolicious::Lite?__

    app->renderer->root('/foo/bar')

__What's an attribute 'name' for? In routes. Where should I use it?__

    $self->url_for('name')

__Is it possible with Mojo::JSON to check the syntax?__

No. No syntax check. But it sets ->error attribute on errors.

__Whats best practice for mojo and mod_perl2?__

__How to get a list of all names only of parameters?__

    my @names = keys %{req->params->to_hash};

or
    my @names = $req->param;

__Are you marcus ramburg?__

    <@marcus> huh?
    <@marcus> I
    <@marcus> am
    <@marcus> not
    <@marcus> ramburg!

Please try to avoid doing mistakes in people's names. This enrages them. If you are not sure, use a nickname.

__Do we have usable json in mojo yet?__

Of course we do. Take a look at Mojo::JSON.

__What is epl short for? English premier league?__

Embedded Perl lite.

__I want to customize Mojo::Template encoding. Is there the way to do it through Mojolicious?__

There is encoding option.

__What's the latest status on mojolicious documentation?__

__I see you're about keeping it free of dependencies - how do you feel about people developing extensions?__

Extenstions are very welcome. There are already many of them. Search CPAN for MojoX namespace.

__I don't understand waypoint and bridge. When do I use waypoint and bridge?__

Bridges

Sometimes it is necessary to call a method after another (e.g. authorization, data processing). That's what bridge is for.

    # /blog
    $r->bridge->to(controller => 'foo', action =>'auth')
      ->route('/blog')->to(action => 'list');

Foo::auth will be called before Foo::list. If Foo:auth does not return a true value, the chain will be broken and return without Foo::list being called.

Waypoints

Waypoint is something in between bridges and nested routes. It can match even if it's not an endpoint, but will behave just like route if children are matching too.

    # /books
    my $b = $r->waypoint('/books')->to(controller => 'books', action => 'list');

    # /books/1
    $b->route('/:id', id => qr/\d+/)->to(action => 'view');

__What should I use html_escape and xml_escape for?__

xml_escape is the faster and simpler version of html_escape which escapes every single entitie. html_escape uses all xhtml 1.0 entities, xml_escape only & < > " '.

__How's the new docs coming along?__

__How to render data/plainfile.html in template?__

    <%= $self->render_partial('data/plainfile.html') %>

__Web in a box?__

    <@sri> don't push the button!
    <@sri> no wait, that was a different box...

__How to get an absolute path of app home?__

    app->home;

__How to add charset utf-8 by default in headers?__

    $self->renderer->types->type(html => 'text/html; charset=utf-8');

__How do I get params inside a controller?__

    $self->req->param('foo');

__Where is the test server's document root? Is it just in whatever directory you invoke it?__

__Anyone know how I can get the remote IP address within a Mojo controller?__

    $self->tx->remote_address;

__How do I access the transaction from within a handler in the controller?__

    $self->tx;

__Has anyone used Mojolicious and the Petal templating system together? Would it be tricky to do?__

You would have to build a custom renderer like MojoX::Renderer::TT.

__How to use MyApp::CARROT as controller?__

Since CARROT is not camelcase and can't be automatically converted from carrot, you should use

    ->route(...)->to(class => 'CARROT');

__Anyone know how I can stuff raw HTML into a Mojolicious template without it getting escaped?__

    <%== ...

__Does ep stand for something?__

Embedded Perl.

__So I can easily convert a CGI.pm based app to mojo?__

__When do you plan 1.0?__

Right after the documentation.

__Does anyone know why I might be having trouble accessing files within my 'public' directory?  For some reason I'm unable to get my public js and css files to load.__

__I have 5 actions for one route. And I have 5 $self->render( ... ) at the end of every action. ;) How to render universally? For example to run a function to render depending on a parameter from stash?__

__Bridge is used before route. Is it available to run action after route?__

__how do I set a cookie from a mojolicious controller?__

__How do I do an external redirect from a controller?__

    $self->redirect_to('my-action');
    $self->redirect_to('http://absolute.url');

__Does setting $self->res->body bypass the rendering in MojoX::Dispatcher::Routes::dispatch?__

No, response code should be added also. But for rendering a text

    $self->render_text('foo');

can be used.

__What happens when you do $tx->pause? Switching to other transactions?__

Flow just goes on, it sets the tx in hibernate mode (can't write) and the handler will end normally.

__Anyone have a favourite i18n module that's nice to use / plays nice with mojo(licious)?__

Take a look at MojoX::Locale::Maketext.

__Is there a Mojo modules page?__

Not yet. Feel free to contribute.

__Going for the advent calendar plan after all?__

    <@sri> marcus: no way

__Doesn't mojo have an async http client built in now?__

Yes. Mojo::Client is fully async.

__Any ideas about how hard it would be to embed a mojo app in a catalyst app?__

There is Catalyst::Engine::Mojo, it could be outdated, but is a good example.

__How to create a "https" link via url_for?__

__Is it possible to create a full link (with http://) via url_for?__

    $self->url_for('some-action')->to_abs;

__MP3 streaming client?__

    #!/usr/bin/perl

    use Mojo::Client;
    use Mojo::Transaction::HTTP;

    my $url = shift @ARGV;
    my $handler = 'mpg123 -';

    open(HANDLER, "|$handler") or die "Cannot pipe input to $handler: $!\n";

    my $tx = Mojo::Transaction::HTTP->new;
    $tx->req->method('GET');
    $tx->req->url->parse($url);
    $tx->res->body(
        sub {
            my ($res, $chunk) = @_;
            print HANDLER $chunk;
        }
    );

    Mojo::Client->new->process($tx);

    close HANDLER;

__How to use ladders?__

__Is anybody using Mojo for high-traffic sites? What's the performance like?__

__Is there a way to access the route's name from within the .ep templates?__

__Mojolicious rules. Why people in the Perl world don't understand this simple thing?__

__What is the difference between dispatch() and process()?__

__Can I create POST request emulating HTML form?__

__Are there any bigger example application? Or even real ones?__

__Could someone tell me how to run Mojolicious with fastcgi?__

__--address. It can't listen unix socket?__

__What about nginx & Mojo fcgi? Must it have anything special in fastcgi parameters?__

__so what would be the fastest way to get up to speed on Mojo?__

__I want only 2 or 3 processes of fcgi, how to run? I tried --servers 2, but again get 6 processes.__

__btw, this is the most jabber I've seen on #mojo in a week. is it usually quiet?__

__Is there a Mojo component to manage user authentication and sessions ?__

__why is mojo telling me "It looks like you don't have the Mojo Framework__
__installed." even though I just installed it?__

__how do I tell Mojolicious::Lite that the content I'm about to send is "application/xml"?__

__With $client->post, where do I put my post data in?__

__How can i determine name of current route?__

__How to reload mojolicious application? What a signal should I send to a process?__

__is there somewhere to paste?__

__I just want to run a Mojo app on a single location within a site... is this possible?__

__How can one add additional params when loading a plugin?__

__does Mojo::Client follow redirects?__

__Can you explain to newbie how can i pass additional fcgi params to mojolicious app?__

__Is access to raw environment not available?__

__How to run Mojolicious::Lite on different address:port?__

__Is there a page with list of sites build on mojo?__

__does anyone know if it is possible to use Template::Toolkit with Mojolicious::Lite?__

__Is there way to clear template cache of mojo server without restarting server?__

__how can one load a plugin with a different namespace?__

__inside mojo, is there a better way to report an error but calling die?__

__Are there any thoughts or ideas about using Mojo with Moose or at least Mouse?__

__is there a startup sub for mojo lite apps?__

__Could someone explain to me what waypoint() does?__

__Is there a way to specify query parameters in url_for, or do I need to handle that myself?__

__all new to mojo, any tutorials about ?__

__do you tweet?__

__btw are u looking for contributors, if so how ?__

__when should one use charset plugin?__

__can someone make this work?__

__somehow set headers having a hashref without iterating?__

__Do you plan have a talk about Mojo on any Perl workshop or YAPC?__

__are there reserved stash keys?__

__Why post_form, not just form or post_data?__

__How to use other than UTF-8 encoding in MojoX::Renderer::TT?__

Here is an example how to serve cp1251 templates (by Alexander *nordicdyno* Orlovskiy)

    MojoX::Renderer::TT->build(
        mojo             => $self,
        template_options => {UNICODE => 0, ENCODING => 'windows-1251'}
    );

