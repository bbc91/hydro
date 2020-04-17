<template>
    <Page actionBarHidden="true">
        <TabView
            android:tabBackgroundColor="#4aa9ee"
            android:tabTextColor="#ffffff"
            android:selectedTabTextColor="#ffffff"
            androidSelectedTabHighlightColor="#ffffff"
        >
            <TabViewItem class="fal menuButton" title.decode="&#xf043; Вода">
                <GridLayout columns="*" rows="*">
                    <Label class="fal" col="0" row="0" />
                </GridLayout>
            </TabViewItem>
            <TabViewItem class="fal menuButton" title.decode="&#xf1da; История">
                <GridLayout columns="*" rows="*">
                    <Label
                        class="message"
                        text="Tab 2 Content"
                        col="0"
                        row="0"
                    />
                </GridLayout>
            </TabViewItem>
            <TabViewItem class="fal menuButton" title.decode="&#xf013; Настройки">
                <GridLayout columns="*" rows="*">
                    <Label
                        class="message"
                        text="Tab 3 Content"
                        col="0"
                        row="0"
                    />
                </GridLayout>
            </TabViewItem>
        </TabView>
    </Page>
</template>

<script>
export default {
    data() {
        return {};
    },
};
</script>

<style scoped></style>
