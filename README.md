<div id="reemodiv"></div>
<script src="https://static.reemo.io/reemo.min.js"></script>

<script>
    function onExtraAction() {
        console.log('extra action clicked');
    }

    window.onload = () => {
        // Initialize Reemo.js
        const reemo = new Reemo.WebClient();

        // Events
        reemo.on('created', () => {
            console.log('WebClient created');
        });
        reemo.on('beforeDestroy', () => {
            console.log('WebClient is beeing destroyed');
        });
        reemo.on('state', ({state, error}) => {
            console.log(`State Changed: ${state}, Error: ${error}`);
        });
        reemo.on('back', () => {
            console.log('back button pressed');
        });
        reemo.on('retry', () => {
            console.log('retry button pressed');
        });

        // Initialize the DOM
        reemo.init('reemodiv', {
            backButton: true,
            retryButton: true,
            extraMenu: [{
                label: 'Extra Options',
                type: 'options',
                options: [{
                    label: 'Extra Option',
                    type: 'action',
                    action: onExtraAction,
                }]
            }, {
                label: 'Reemo.io',
                type: 'link',
                link: 'https://reemo.io',
            }]
        });

        // Connect to the computer provided by your website's API (connected to the Reemo API)
        reemo.connect(computer);
    };
</script>
