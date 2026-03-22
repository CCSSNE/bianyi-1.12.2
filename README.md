**This repository focuses solely on compilation compatibility, enabling the source code to directly build IPA and APK files within the action.**

Testing revealed that everything else works normally; only the PAL Square and login features are unusable. Since the original release.yml is not hardcoded but retrieves configuration from GitHub Actions:

SUPABASE_URL=${{ vars.SUPABASE_URL }}

SUPABASE_ANON_KEY=${{ secrets.SUPABASE_ANON_KEY }}

PALSHUB_API_BASE_URL=${{ vars.PALSHUB_API_BASE_URL }}%%

**PALSHUB_API_BASE_URL**
I know the official value is https://palshub.ai; it directly determines the base URL for the public Pals API. This can be easily filled in, but this repository will not fill it because its goal is only to make compilation possible. My actual forked repository includes this fix. The reasons are as follows:

1. The official site is indeed https://palshub.ai Source: PalsHub website

3. Its homepage clearly states “AI Pals for PocketPal AI,” which is the official public site. In the original open repository, .env.example directly sets the default value to PALSHUB_API_BASE_URL=https://palshub.ai Source: a-ghorbani/pocketpal-ai/.env.example

**SUPABASE_URL**
Although I know it “should be” a certain Supabase project address, I don’t know which exact project the original version is using. The .env.example only contains a placeholder: https://your-project.supabase.co. Since this is not an actual value, I cannot guess blindly.

**SUPABASE_ANON_KEY**
Similarly, I don’t know the true value either and cannot write it randomly by guessing.
You can decompile the official released APK to find these hidden parameters and recover the login functionality.
