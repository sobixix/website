(function($) {
    "use strict";


    var rtl_is = false;
    var rtl_skill = 'left';
    if (mim) {
        if (mim['check_rtl']==1) {
           var rtl_is = true; 
           var rtl_skill = 'right'; 
        } else {
            var rtl_is = false; 
            var rtl_skill = 'left'; 
        }
    }

    // Sticky Menu Bar
    $(window).on('scroll', function() {
        var scroll = $(window).scrollTop();
        var AESticky = $('.active-sticky');
        if (scroll < 245) {
            AESticky.removeClass("is-sticky");
        } else {
            AESticky.addClass("is-sticky");
        }
    });


    // Smooth scroll
    $('.smooth-scroll a[href*="#"]:not([href="#"])').click(function() {
        if (location.pathname.replace(/^\//, '') == this.pathname.replace(/^\//, '') && location.hostname == this.hostname) {
            var target = $(this.hash);
            target = target.length ? target : $('[name=' + this.hash.slice(1) + ']');
            if (target.length) {
                $('html, body').animate({
                    scrollTop: target.offset().top
                }, 750);
                return false;
            }
        }
    });


    // One page Nav
    function onePageNav($selector) {
        var $navSelector = $($selector);
        $navSelector
        .not('[href="#"]')
        .not('[href="#0"]')
        .click(function(event) {
            if ( location.pathname.replace(/^\//, '') === this.pathname.replace(/^\//, '') && location.hostname === this.hostname ) {
                var target = $(this.hash);
                target = target.length ? target : $('[name=' + this.hash.slice(1) + ']');

                $navSelector.removeClass("active");
                if( target.length) {
                    if($(this)[0].hash.slice(1) === target[0].id) {
                        $(this).addClass("active");
                    } else {
                        $(this).removeClass("active");
                    }
                }
                
                if (target.length) {
                    event.preventDefault();
                    $('html, body').animate({
                        scrollTop: target.offset().top - 80
                    }, 1000);
                }
            }
        });

        $navSelector.each(function(event) {
            var target = $(this.hash);
            if( target.length) {
                if(location.hash.slice(1) === target[0].id) {
                    $(this).addClass("active");
                } else if(!location.hash) {
                    
                } else {
                    $(this).removeClass("active");
                }
            }
        });

        function onScroll(event){
            var scrollPos = $(document).scrollTop();
            $navSelector.each(function () {
                var currLink = $(this);
                if(currLink[0].hash !== "" && $(currLink[0].hash).position() !== undefined) {

                    var $getNavHas = $(currLink).prop('href').split('#')[1],
                        $getSection = $('#' + $getNavHas); 

                    $getSection.each(function() {
                        var $topPos = $(this).offset().top,
                            $topPosRound = Math.round($topPos - 80 ),
                            $presentPos = Math.round(scrollPos);

                        if ($topPosRound <= $presentPos && $topPosRound + $(this).height() > $presentPos) {
                            $(currLink).parent().addClass("active"); 
                        } else {
                            $(currLink).parent().removeClass("active");
                        }
                    });
                } else {
                    return false;
                }
            });
        }
        $(document).on("scroll", onScroll);      
    }

    onePageNav('.mim-one-page ul li a');

    var CloseMu = $('.close-menu');
    var ExMu = $('.mainmenu-expand');
    var ExMuOp = $('.expand-menu-open');
    CloseMu.on('click', function() {
        $(this).parent(ExMu).removeClass('slide_right');
    });
    ExMuOp.on('click', function() {
        CloseMu.parent(ExMu).addClass('slide_right');
    });

    $(document).on('click', function(e) {
        var $authorSelectorDoc = $('.mainmenu-expand, .expand-menu-open');
        if (!$authorSelectorDoc.is(e.target) && $authorSelectorDoc.has(e.target).length === 0) {
            $('.mainmenu-expand').removeClass("slide_right");
        }
    });

    var $submenu = $('.mainmenu-box.onepage-nev.mim-one-page ul li').has('.sub-menu');
    $submenu.prepend("<span class='menu-click'><i class='menu-arrow fa fa-plus'></i></span>");
    var $mobileSubMenuOpen = $(".menu-click");
    $mobileSubMenuOpen.on("click", function() {
        var $self = $(this);
        $self.siblings(".sub-menu").slideToggle();
        $self.children(".menu-arrow").toggleClass("menu-extend");
    });


    if ( rtl_is == true ) { 
        // Progress Bar
        var ProWey = $('.skill-progress');
        if (ProWey.length > 0) {
            ProWey.waypoint(function() {
                jQuery('.skill-bar').each(function() {
                    jQuery(this).find('.progress-content').animate({
                        width: jQuery(this).attr('data-percentage')
                    }, 2000);

                    jQuery(this).find('.progress-mark').animate({
                        right: jQuery(this).attr('data-percentage')
                    },
                    {
                        duration: 2150,
                        step: function(now, fx) {
                            var data = Math.round(now);
                            jQuery(this).find('.percent').html(data + '%');
                        }
                    });
                });
            }, {
                offset: '90%'
            });
        };
    } else {
        // Progress Bar
        var ProWey = $('.skill-progress');
        if (ProWey.length > 0) {
            ProWey.waypoint(function() {
                jQuery('.skill-bar').each(function() {
                    jQuery(this).find('.progress-content').animate({
                        width: jQuery(this).attr('data-percentage')
                    }, 2000);

                    jQuery(this).find('.progress-mark').animate({
                        left: jQuery(this).attr('data-percentage')
                    },{
                        duration: 2150,
                        step: function(now, fx) {
                            var data = Math.round(now);
                            jQuery(this).find('.percent').html(data + '%');
                        }
                    });
                });
            }, {
                offset: '90%'
            });
        };
    }


    //Portfolio Filtering
    var ProjMli = $('.portfolio-menu li');
    var ProjGrid = $('.portfolio-grid');
    ProjMli.on('click', function() {
        ProjMli.removeClass("active");
        $(this).addClass("active");
        var selector = $(this).attr('data-filter');
        ProjGrid.isotope({
            filter: selector,
            animationOptions: {
                duration: 750,
                easing: 'linear',
                queue: false,
            }
        });
    });



    // Fancybox Popup
    $('.fancybox').fancybox({
        openEffect: 'fade',
        closeEffect: 'fade',
        padding: 0,
        closeBtn: true,
        helpers: {
            title: {
                type: 'inside'
            },
            buttons: {},
            overlay: {
                locked: false
            }
        }
    });

    $(".fancybox-single").fancybox({
        openEffect  : 'none',
        closeEffect : 'none'
    });

    $(".various").fancybox({
        'padding': 0,
        maxWidth: 800,
        maxHeight: 600,
        fitToView: false,
        width: '70%',
        height: '70%',
        autoSize: false,
        closeClick: false,
        openEffect: 'fade',
        closeEffect: 'fade'
    });


    // Slick
    $('.one-item').owlCarousel({
        loop: true,
        items: 1,
        dots: true,
        nav: false,
        rtl: rtl_is,
    });


    // Scroll To Top
    $.scrollUp({
        scrollText: '<i class="zmdi zmdi-chevron-up"></i>',
        easingType: 'linear',
        scrollSpeed: 900,
        animation: 'fade'
    });

})(jQuery);


// Loading Portfolios
jQuery(window).on('load', function() {
    var preeLoad = jQuery('#loading');
    preeLoad.fadeOut(1000);
    var IsoGriddoload = jQuery('.portfolio-grid');
    IsoGriddoload.isotope({
        itemSelector: '.grid-item',
        masonryHorizontal: {
            rowHeight: 100
        }
    });
});