Tired of having to deal with glitchy, unrealiable height with your columns in whatever 
framework you use to do web development? So was I, so I decided to create a robust 
system to prototype spacing, height, typography, and soon to be more stuff because 
I modify stuff whenever it needs to be. 

This is a little Sass library, so obviously it must be used with that. It uses a 
minimalistic, C style, extremely explicit syntax to generate rows for EVERY style of 
device. Specific devices I allow are Phone, which is a major breakpoint representing
small mobile devices, tablet, a minor breakpoint representing larger mobile devices
(including tablets AND phablets, and even smaller laptops.), laptop which is used
for small mobile computers and lower resolution Desktops. Desktop, which is used for 
"normal" desktops, huge which is used for ultra hi resolution desktops. I also include
a lowHeight type for when a user decideds to shrink a window to very small size, which
causes the small, mobile displays to occur, even though the window is still wide.

--------> LIST OF TYPES <------
        ->phone
        ->tablet
        ->desktop
        ->huge
        ->lowHeight

--------> Important -----------!
        It is very important
        that our styles are
        declared in this order,
        otherwise our output
        media queries will not
        scale correctly.

But what are these if we cannot use them on our div classes? I include multiple 
functions that we can use to actually modify how our divs appear at different widths.
Note that this "framework" doesn't depend on the height of the screen, except with 
the lowHeight. Rather it depends on the width to apply logic based on how large or 
screen is.

    ---->LIST OF CURRENT FUNCTIONS <-----
        ------------------------------\
        ->row-generate(row-size, type)\
        ------------------------------\
       
                *USAGE*
.header{
    @include row-generate(6, phone);
    @include row-generate(6, tablet);
    @include row-generate(12, desktop);
    @include row-generate(12, huge);
    @include row-generate(6, lowHeight);
}
        ------------------------------\
        ->top-generate(row-size, type)\
        -------------------------------

------------->Think of this as Bootstraps col-offset-**-##!!

                *USAGE*
.header{
    @include top-generate(6/2 - 1.6, phone);
    @include top-generate(6/2 - 1.6, tablet);
    @include top-generate(12/2 - 1.6, desktop);
    @include top-generate(12/2 - 1.6, huge);
    @include top-generate(6/2 - 1.6, lowHeight);
        
            !!Notice how I divide it by two, that means we have a 
            vertically centered div and that minus gives us an 
            offset. We can modify that offset based on how texts
            changes while our design responds!!

        ---------------------------------------------------------------------\
        ->typography-generate(type, size, typeOfSize, (optional) font-family)\
        ---------------------------------------------------------------------\

            *USAGE*
.header 
{
    .collection
    {
        @include typography-generate(phone, 26px, vw);
        @include typography-generate(desktop, 3em, em, $font-stack-different);
        @include typography-generate(huge, 3em, em);
        @include typography-generate(lowHeight, 26px, vw);
    }
}

-------->you may see the I have your unit as input: that is to make it 
        easy for anyone working on the website to know and explicitly 
        say KEEP IT AT THIS UNIT.!!


    It's a small group of functions, but I have already found awesome uses for this 
and more will come as I put it into Szism and refine it.





