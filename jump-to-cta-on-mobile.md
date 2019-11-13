```
<style type="text/css">@media only screen and (min-width: 600px) {
        div#mobileScrollerFooter {
            display: none;
        }
    }
    div#mobileScrollerFooter {
        position: fixed;
        bottom: 0;
        background-color: #fff;
        color:#fff;
        width: 100%;
        padding: 1rem;
        z-index: 1000;
        text-align: center;
        box-sizing: border-box;
    }
    a#mobileScroller {
        cursor: pointer;
        display: block;
        color: white;
    }
</style>
<script src="https://code.jquery.com/jquery-3.4.1.min.js"></script><script>
    $(document).ready(function() {
        // Insert the button into the HTML
        var buttonText = "Sign the letter";
        var buttonHTML = "<div id='mobileScrollerFooter'><a class='button' id='mobileScroller'>" + buttonText + "</a></div>"
        $( buttonHTML ).insertAfter( ".wrap" );
        var $floatingButton = $("div#mobileScrollerFooter");
        // Where the floating button should slide to
        var $slideTo = $(".breakout-shaded");
        var $slideToPosition = $slideTo.position();
        // Check window width
        if ( $( document ).width() > 600 ) {
            $floatingButton.hide();
        } else {
            // If button clicked, scroll
            $floatingButton.find(".button").click(function() {
                $([document.documentElement, document.body]).animate({
                    scrollTop: $slideTo.offset().top
                }, 2000);
            });
            // Hide button if just above or below target
            $(window).scroll(function(){
                if ( $(window).scrollTop() > ( $slideToPosition.top - 200 ) ) {
                    $floatingButton.slideUp("slow");
                } else {
                    $floatingButton.slideDown("slow");
                }
                
            });
        }
    });
</script>
```
