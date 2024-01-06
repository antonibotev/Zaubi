<script>
    // Mouseover effects for star detail in the hero section
    document.addEventListener('DOMContentLoaded', function() {
        var starDetail = document.querySelector('.star-detail');
        var heroSection = document.querySelector('.hero-section');

        if (starDetail && heroSection) {
            starDetail.addEventListener('mouseover', function() {
                heroSection.classList.add('hero-star-detail');
            });

            starDetail.addEventListener('mouseout', function() {
                heroSection.classList.remove('hero-star-detail');
            });
        }
    });

    // GSAP animations for various elements
    const elements = [
        ...document.querySelectorAll(".all-caps-label-transparent-inner"),
        ...document.querySelectorAll(".h1-hero-section"),
        ...document.querySelectorAll(".hero--section-caption"), // ...document.querySelectorAll(".hero-section-caption") - ako iskam da raboti da slova tova ime / pisha greshno ime na vtoria dizain na houma
        ...document.querySelectorAll(".bouncy-button")
    ];

    elements.forEach((element, index) => {
        gsap.fromTo(element, 
            { y: 16 },
            {
                y: 0, 
                ease: "power2.out",
                scrollTrigger: {
                    trigger: element,
                    start: "top 200%",
                    toggleActions: "play none none none"
                },
                duration: 0.4,
                delay: index * 0.1
            }
        );

        gsap.fromTo(element, 
            { opacity: 0 },
            {
                opacity: 1, 
                ease: "none",
                scrollTrigger: {
                    trigger: element,
                    start: "top 200%",
                    toggleActions: "play none none none"
                },
                duration: 0.6,
                delay: index * 0.1
            }
        );
    });

    // Additional GSAP animations for different triggers
    gsap.utils.toArray(".first-trigger-line, .second-trigger-line, .third-trigger-line").forEach((element) => {
        let delay;
        if (element.classList.contains("first-trigger-line")) {
            delay = 0.1;
        } else if (element.classList.contains("second-trigger-line")) {
            delay = 0.3;
        } else {
            delay = 0.5; // Assume 'third-trigger-line'
        }

        gsap.fromTo(element, 
            { y: 24 },
            {
                y: 0, 
                ease: "power2.out",
                scrollTrigger: {
                    trigger: element,
                    start: "top 90%",
                    toggleActions: "play none none none"
                },
                duration: 0.4,
                delay: delay
            }
        );

        gsap.fromTo(element, 
            { opacity: 0 },
            {
                opacity: 1, 
                ease: "none",
                scrollTrigger: {
                    trigger: element,
                    start: "top 90%",
                    toggleActions: "play none none none"
                },
                duration: 0.4,
                delay: delay
            }
        );
    });

    // Page Transition logic
    $(".content-wrapper").addClass("first");
    let nextPageLink;

    $(".portfolio-link-container").on("click", function(e) {
        e.preventDefault();
        nextPageLink = $(this).attr("href");

        $.ajax({
            url: nextPageLink,
            success: function(response) {
                let element = $(response).find(".content-wrapper").addClass("second");
                $(".main-wrapper").append(element);
            },
            complete: function() {
                pageTransition();
            }
        });
    });

    function pageTransition() {
        $("html").addClass("animating");

        let tl = gsap.timeline({ onComplete: updatePage });

        tl.from(".content-wrapper.second", {
            y: "110vh",
            delay: 0,
            duration: 0.6,
            ease: "power4.out"
        });
    }

		$(".portfolio-link-container").on("click", function(e) {
        // Save current scroll position
        sessionStorage.setItem('scrollPosition', window.scrollY || document.documentElement.scrollTop);
        // Rest of your AJAX call and navigation code...
    });

		document.addEventListener('DOMContentLoaded', function() {
        var savedScrollPosition = sessionStorage.getItem('scrollPosition');
        if (savedScrollPosition) {
            window.scrollTo(0, parseInt(savedScrollPosition));
        }
        // Rest of your DOMContentLoaded code...
    });



    function updatePage() {
        window.location = nextPageLink;
    }
</script>
