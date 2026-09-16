window.quizConfig = {
  version: "2026-04-27",
  startId: "q1_useCase",
  activeConnectVariant: "s7",
  deviceVariants: {
    connect: {
      connect: {
        label: "Connect",
        param: "connect",
        imageUrl:
          "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6887f2ec5c894c7fd201e4d4_connect-dec-tree-100px-w.avif",
      },
      s7: {
        label: "Soberlink 7.0",
        param: "s7",
        imageUrl:
          "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/68cd9c1923caa0a031c70739_soberlink7-dec-tree-100px-w.avif",
      },
    },
    "cellular 2": {
      default: {
        label: "Cellular 2",
        param: "cellular 2",
        imageUrl:
          "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6887f2ecf01bc5160d57ba58_cellular-2-dec-tree-100px-w.avif",
      },
    },
  },
  modals: {
    concernedPartyInfo: {
      titleHtml: "<strong>What is a Concerned Party?</strong>",
      bodyHtml:
        "A <span class='u-bold'>“Concerned Party,” often</span> a co-parent, guardian, or attorney, is <span class='u-bold'>someone who helps play a supportive role</span> in the child’s wellbeing.",
      items: [
        {
          img: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69dd75d9e724d5149dfe7fa4_cp-2.avif",
            alt: "Co-parent",
          },
          labelHtml: "Co-parent",
        },
        {
          img: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69dd75d9415ffa7178741b99_cp-1.avif",
            alt: "Guardian",
          },
          labelHtml: "Guardian",
        },
        {
          img: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69dd75d9b525cb2e87077014_cp-3.avif",
            alt: "Attorney",
          },
          labelHtml: "Attorney",
        },
      ],
    },
    contactInfo: {
      titleHtml: "<strong>What is a Contact?</strong>",
      bodyHtml:
        "A “Contact” is a person who will receive the results. This is typically a family member, friend, or treatment professional.",
    },
    womanStory: {
      titleHtml:
        "Choosing Support Over Stigma: Investing in Solutions That Work Story",
      videoUrl: "https://www.youtube.com/embed/2ZjxjjW1SZA",
    },
    manStory: {
      titleHtml: "When Building Back Trust is in the Best Interest of the Kids",
      videoUrl: "https://www.youtube.com/embed/C6nturMK390",
    },
    maxAndCami: {
      titleHtml: "How One Couple Rebuilt Trust After Addiction with Soberlink",
      videoUrl: "https://www.youtube.com/embed/QrmptnNaV7A",
    },
    emailResults: {
      titleHtml: "<strong>Email me my results</strong>",
      kind: "emailForm",
    },
  },
  nodes: {
    intro_start: {
      id: "intro_start",
      type: "start",
      text: "Answer a few questions to help us find the best device and plan for your needs.",
      primaryCta: { label: "Start", nextId: "q1_useCase" },
    },
    q1_useCase: {
      id: "q1_useCase",
      type: "singleChoice",
      text: "How will you be using Soberlink?",
      options: [
        {
          value: "submitTests",
          labelHtml: "I will be submitting tests.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69b1d7bbdcbd0ec72e582683_Icon-cellular-device-v2.avif",
            alt: "device icon",
          },
          nextId: "qA2_reasons_submitter",
        },
        {
          value: "receiveResults",
          labelHtml: "I will be receiving test results.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738614970aa5b99ef4e_icon-i-will-receive-texts.avif",
            alt: "phone icon",
          },
          nextId: "qB2_reasons_receiver",
        },
      ],
    },
    postPlan_router: {
      id: "postPlan_router",
      type: "router",
      rules: [
        {
          whenEquals: { nodeId: "q1_useCase", value: "submitTests" },
          nextId: "qD1_paymentPreference",
        },
        {
          whenEquals: { nodeId: "q1_useCase", value: "receiveResults" },
          nextId: "qB_devicePurchaser",
        },
      ],
      defaultNextId: "qB_devicePurchaser",
    },
    qA2_reasons_submitter: {
      id: "qA2_reasons_submitter",
      type: "multiChoice",
      text: "Select <span class='u-bold' style='color: #00abdf;'>all</span> the reason(s) you need monitoring. You can select multiple.",
      options: [
        {
          value: "childCustody",
          labelHtml: "Child Custody (Family Law)",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f105e3b251bf554a158_child%20custody.png",
            alt: "Child custody",
          },
        },
        {
          value: "marriageRelationship",
          labelHtml: "Marriage/Relationship",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f10e36776c1e40d98f8_marriage%20relationships.png",
            alt: "Relationship",
          },
        },
        {
          value: "employment",
          labelHtml: "Employment",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f12c0c3add2adbd0a08_work.png",
            alt: "Employment",
          },
        },
        {
          value: "voluntaryAccountability",
          labelHtml: "Voluntary/Accountability",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69f8f8e2b32a01c4581c6a45_icon-volunteer-1.avif",
            alt: "Voluntary",
          },
        },
        {
          value: "other",
          labelHtml: "Other",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69fa62f67e70f42de93f514e_other_icon_30px_antialiased.png",
            alt: "Other",
          },
        },
      ],
      rules: [
        { whenIncludesAnyOf: ["childCustody"], nextId: "qA3_custody_context" },
        {
          whenIncludesAnyOf: [
            "employment",
            "marriageRelationship",
            "voluntaryAccountability",
            "other",
          ],
          nextId: "qA3_share_contacts_submitter",
        },
      ],
      // defaultNextId: "qA3_incomplete_other",
    },

    qA3_custody_context: {
      id: "qA3_custody_context",
      type: "singleChoice",
      text: "We’ll tailor a plan that best fits your needs. Which option feels most like your situation?",
      options: [
        {
          value: "proactiveFalselyAccused",
          labelHtml: "I am being falsely accused or preparing for a case.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f1061c8412f197bf530_Accused.png",
            alt: "thumbs down",
          },
          nextId: "qA4_testingFrequency_submitter",
        },
        {
          value: "proveSoberParentingTime",
          labelHtml: "I need to prove I am sober during parenting time.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f127fc27e2065acf64e_Sober%20PT.png",
            alt: "person and check icons",
          },
          nextId: "qA4_testingFrequency_submitter",
        },
        {
          value: "fullAbstinenceKeepKids",
          labelHtml: "I need to prove that I am sober every day.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f106ab22d06aa2f7922_Abstinence.png",
            alt: "stop sign",
          },
          nextId: "qA5L2_intro_submitter",
        },
      ],
    },
    // qA3a_proactiveFalselyAccusedQuote: {
    //   id: "qA3a_proactiveFalselyAccusedQuote",
    //   type: "quote",
    //   headlineHtml:
    //     "You're not alone.<br/>Many people have used Soberlink for the same reason. <br/><br/>Here's a story from a real Soberlink client:",
    //   subtitleHtml:
    //     "It was submitted to the courts that my past relationship with alcohol could interfere with my ability to parent. When it becomes someone's word against someone else's word, decisions can be made that aren't always right. Soberlink made it undeniable that the things that I was saying about my own recovery were the truth.",
    //   person: {
    //     name: "Evan",
    //     attribution: "Soberlink Client",
    //   },
    //   primaryCta: {
    //     label: "Continue",
    //     nextId: "qA4_testingFrequency_submitter",
    //   },
    // },
    // qA3a_proveSoberParentingTimeQuote: {
    //   id: "qA3a_proveSoberParentingTimeQuote",
    //   type: "quote",
    //   headlineHtml:
    //     "You're not alone.<br/>Many people have used Soberlink for the same reason. <br/><br/>Here's a story from a real Soberlink client:",
    //   subtitleHtml:
    //     "I had picked my son up from school and I had been drinking. My husband had reached his limit and ended up filing for divorce. My attorney recommended that I use Soberlink to prove to the court that I was able to be with my children without drinking. It puts my husband's mind at ease knowing that there is that accountability piece.",
    //   person: {
    //     name: "Sarah",
    //     attribution: "Soberlink Client",
    //   },

    //   primaryCta: {
    //     label: "Continue",
    //     nextId: "qA4_testingFrequency_submitter",
    //   },
    // },
    // qA3a_fullAbstinenceKeepKidsQuote: {
    //   id: "qA3a_fullAbstinenceKeepKidsQuote",
    //   type: "quote",
    //   headlineHtml:
    //     "You're not alone.<br/>Many people have used Soberlink for the same reason. <br/><br/>Here's a story from a real Soberlink client:",
    //   subtitleHtml:
    //     "My ex-husband had sole custody of my kids because of my alcohol abuse, and I was only allowed to see them under strict provisions. My parenting plan required alcohol testing. Soberlink is the best alcohol monitoring method there is for someone like me who's seriously alcoholic and needs daily accountability. It's worth every penny. You can't put a price on time with your child.",
    //   person: {
    //     name: "Krista",
    //     attribution: "Soberlink Client",
    //   },

    //   primaryCta: {
    //     label: "Continue",
    //     nextId: "qA4_testingFrequency_submitter",
    //   },
    // },
    qA4_testingFrequency_submitter: {
      id: "qA4_testingFrequency_submitter",
      type: "singleChoice",
      text: "Which option sounds most like you?",
      size: "lg",
      options: [
        {
          value: "everyDay",
          labelHtml:
            "<span class='u-normal'>I am willing or required to</span> test every day.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f10cf15960ad2f62cb4_daily%20testing.avif",
            alt: "calendar with all days highlighted icon",
          },
          badge: {
            label: "EXPERTS SUGGEST TESTING EVERY DAY",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          nextId: "qA5L2_intro_submitter",
        },
        {
          value: "parentingDaysOnly",
          labelHtml:
            "<span class='u-normal'>I</span> only <span class='u-normal'>need to</span> test on parenting days.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f106563beec4dbc11d9_icon-parenting-only-testing%201.avif",
            alt: "calendar icon with only several days highlighted",
          },
          nextId: "qA5L1_intro_submitter",
        },
      ],
    },
    qA5L2_intro_submitter: {
      id: "qA5L2_intro_submitter",
      type: "info",
      headlineHtml:
        "<span style='font-size: 16px;'>We suggest our</span><br/><span style='color: #00abdf;'>Level 2 - Daily Testing Program</span>",
      textHtml:
        "<span style='font-size: 16px;'>Consistent monitoring, 7 days a week. Testing schedules managed by Soberlink.</span>",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8913be2c8175724ce3d4f_Level-1-Photo%201.avif",
      primaryCta: { label: "Next", nextId: "qA6L2_shareScope_submitter" },
    },
    qA6L2_shareScope_submitter: {
      id: "qA6L2_shareScope_submitter",
      type: "singleChoice",
      introText:
        "To keep everyone informed, your results must be shared with a “Concerned Party”.",
      infoIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a9fcbcf5cd846f8b7e504b_icon%20info.png",
        alt: "Info icon",
        text: "What is a Concerned Party?",
      },
      infoLink: {
        type: "lightbox",
        id: "concernedPartyInfo",
        labelHtml: "Concerned Party info",
      },
      options: [
        {
          value: "concernedOnly",
          labelHtml:
            "<span class='u-normal'>I need my</span> results shared <span class='u-normal'>with my</span> Concerned Party only.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd4bad2f8d698ab385_One%20Person.png",
            alt: "one person",
          },
          nextId: "qA7L2_notify_concernedOnly_submitter",
        },
        {
          value: "concernedAndOthers",
          labelHtml:
            "<span class='u-normal'>I need my</span> results shared <span class='u-normal'>with my</span> Concerned Party and <span class='u-normal'>other</span> contacts.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd9b14c609f0ac6f6f_Two%20People%20%2B.png",
            alt: "two people",
          },
          nextId: "qA7L2_notify_manyContacts_submitter",
        },
      ],
    },
    qA7L2_notify_concernedOnly_submitter: {
      id: "qA7L2_notify_concernedOnly_submitter",
      type: "singleChoice",
      text: "How would you like your progress recognized?",
      choiceLayout: "planCards",
      size: "xlg",
      options: [
        {
          value: "emailNextDay",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed the next day.",
          metaHtml:
            "<div style='color: #26BCD7; font-weight: bold;'>Basic Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "basic",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "Email",
          },
          nextId: "res_plan_level2_basic",
        },
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed in real-time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "plus",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "Email",
          },
          nextId: "res_plan_level2_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed and texted in real-time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "premium",
            cadence: "mo",
          },
          badge: {
            label: "INCLUDES 50% OFF EXPERT TESTIMONY",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_level2_premium",
        },
      ],
    },
    qA7L2_notify_manyContacts_submitter: {
      id: "qA7L2_notify_manyContacts_submitter",
      type: "singleChoice",
      text: "How would you like your progress recognized?",
      choiceLayout: "planCards",
      size: "xlg",
      options: [
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed in real-time.",
          metaHtml:
            "<span class='u-bold' style='color: #00ABDF;'>Plus Plan</span>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "plus",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_level2_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed and texted in real-time.",
          metaHtml:
            "<span class='u-bold' style='color: #1C4A82'>Premium Plan</span>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "premium",
            cadence: "mo",
          },
          badge: {
            label: "INCLUDES 50% OFF EXPERT TESTIMONY",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_level2_premium",
        },
      ],
    },
    qA5L1_intro_submitter: {
      id: "qA5L1_intro_submitter",
      type: "info",
      headlineHtml:
        "<span style='font-size: 16px;'>We suggest our</span><br/> <span style='color: #00abdf;'>Level 1 - Parenting Time Only Program</span>",
      textHtml:
        "<span style='font-size: 16px;'>This plan allows you to test only on days that you need to show proof of sobriety.</span>",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8913be2c8175724ce3d4f_Level-1-Photo%201.avif",
      primaryCta: { label: "Next", nextId: "qA6L1_testingDays_submitter" },
    },
    qA6L1_testingDays_submitter: {
      id: "qA6L1_testingDays_submitter",
      type: "singleChoice",
      text: "Our Level 1 Program includes 20 days of testing each month.",
      options: [
        {
          value: "twentyEnough",
          labelHtml:
            "20 testing days per month is enough. <span class='u-normal'>Extra days at $15 each.</span>",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8be108f33f4d708defb0b_Icon-Calendar-20-Days.avif",
            alt: "calendar icon",
          },
          nextId: "qA7L1_shareScope_submitter",
        },
        {
          value: "needMoreThanTwenty",
          labelHtml: "I need more than 20 testing days a month.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8be1088cb4c64a242b2bd_Icon-Calendar-20-Plus-Days.avif",
            alt: "calendar icon",
          },
          nextId: "res_plan_level1_premium",
        },
      ],
    },
    qA7L1_shareScope_submitter: {
      id: "qA7L1_shareScope_submitter",
      type: "singleChoice",
      introText:
        "To keep everyone informed, your results must be shared with a “Concerned Party.”",
      infoIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a9fcbcf5cd846f8b7e504b_icon%20info.png",
        alt: "More info",
        text: "What is a Concerned Party?",
      },
      infoLink: {
        type: "lightbox",
        id: "concernedPartyInfo",
        labelHtml: "Concerned Party info",
      },
      options: [
        {
          value: "concernedOnly",
          labelHtml:
            "<span class='u-normal'>I need my</span> results shared <span class='u-normal'>with my</span> Concerned Party only.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd4bad2f8d698ab385_One%20Person.png",
            alt: "one person",
          },
          nextId: "qA8L1_notify_concernedOnly_submitter",
        },
        {
          value: "concernedAndOthers",
          labelHtml:
            "<span class='u-normal'>I need my</span> results shared <span class='u-normal'>with my</span> Concerned Party and <span class='u-normal'>other</span> contacts.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd9b14c609f0ac6f6f_Two%20People%20%2B.png",
            alt: "two people",
          },
          nextId: "qA8L1_notify_manyContacts_submitter",
        },
      ],
    },
    qA8L1_notify_concernedOnly_submitter: {
      id: "qA8L1_notify_concernedOnly_submitter",
      type: "singleChoice",
      text: "How would you like your progress recognized?",
      choiceLayout: "planCards",
      size: "xlg",
      options: [
        {
          value: "emailNextDay",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed the next day.",
          metaHtml:
            "<div style='color: #26BCD7; font-weight: bold;'>Basic Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "basic",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "Email",
          },
          nextId: "res_plan_level1_basic",
        },
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed in real-time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "plus",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_level1_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed and texted in real-time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "premium",
            cadence: "mo",
          },
          badge: {
            label: "UNLIMITED TESTING DAYS",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_level1_premium",
        },
      ],
    },
    qA8L1_notify_manyContacts_submitter: {
      id: "qA8L1_notify_manyContacts_submitter",
      type: "singleChoice",
      text: "How would you like your progress recognized?",
      size: "xlg",
      choiceLayout: "planCards",
      options: [
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed in real time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "plus",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "Email",
          },
          nextId: "res_plan_level1_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed and texted in real time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "premium",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          badge: {
            label: "UNLIMITED TESTING DAYS",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          nextId: "res_plan_level1_premium",
        },
      ],
    },
    qA3_share_contacts_submitter: {
      id: "qA3_share_contacts_submitter",
      type: "singleChoice",
      textHtml:
        "Let us help you prove your sobriety. Who would you like to share your results with?",
      infoIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a9fcbcf5cd846f8b7e504b_icon%20info.png",
        alt: "Info icon",
        text: "What is a Contact?",
      },
      infoLink: {
        type: "lightbox",
        id: "contactInfo",
        labelHtml: "Contact info",
      },
      options: [
        {
          value: "oneContact",
          labelHtml:
            "<span class='u-normal'>I need my</span> results shared <span class='u-normal'> with</span> one contact.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd4bad2f8d698ab385_One%20Person.png",
            alt: "one person",
          },
          nextId: "qA4_share_notify_oneContact_submitter",
        },
        {
          value: "moreThanOneContact",
          labelHtml:
            "<span class='u-normal'>I need my</span> results shared <span class='u-normal'>with</span> more than one Contact.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd9b14c609f0ac6f6f_Two%20People%20%2B.png",
            alt: "two people",
          },
          nextId: "qA4_share_notify_manyContacts_submitter",
        },
      ],
    },
    qA4_share_notify_oneContact_submitter: {
      id: "qA4_share_notify_oneContact_submitter",
      type: "singleChoice",
      text: "How would you like your progress recognized?",
      size: "xlg",
      choiceLayout: "planCards",
      options: [
        {
          value: "emailNextDay",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed the next day.",
          metaHtml:
            "<div style='color: #26BCD7; font-weight: bold;'>Basic Plan</div>",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "basic",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_share_basic",
        },
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed in real-time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "plus",
            cadence: "mo",
          },
          badge: {
            label: "MOST POPULAR",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_share_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed and texted in real-time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div> ",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "premium",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_share_premium",
        },
      ],
    },
    qA4_share_notify_manyContacts_submitter: {
      id: "qA4_share_notify_manyContacts_submitter",
      type: "singleChoice",
      size: "xlg",
      choiceLayout: "planCards",
      text: "How would you like your progress recognized?",
      options: [
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed in real-time.",
          metaHtml:
            "<div class='u-bold' style='color: #00abdf;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "plus",
            cadence: "mo",
          },
          badge: {
            label: "MOST POPULAR",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "Email",
          },
          nextId: "res_plan_share_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>My test results will be</span> emailed and texted in real-time.",
          metaHtml:
            "<div class='u-bold' style='color: #1C4A82;'>Premium Plan</div>",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "premium",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "Email and phone",
          },
          nextId: "res_plan_share_premium",
        },
      ],
    },
    qB2_reasons_receiver: {
      id: "qB2_reasons_receiver",
      type: "multiChoice",
      text: "Select <span class='u-bold' style='color: #00abdf;'>all</span> the reason(s) for monitoring. You can select multiple.",
      options: [
        {
          value: "childCustody",
          labelHtml: "Child Custody (Family Law)",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f105e3b251bf554a158_child%20custody.png",
            alt: "Child custody",
          },
        },
        {
          value: "marriageRelationship",
          labelHtml: "Marriage/Relationship",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f10e36776c1e40d98f8_marriage%20relationships.png",
            alt: "Relationship",
          },
        },
        {
          value: "employment",
          labelHtml: "Employment",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f12c0c3add2adbd0a08_work.png",
            alt: "Employment",
          },
        },
        {
          value: "voluntaryAccountability",
          labelHtml: "Voluntary/Accountability",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69f8f8e2b32a01c4581c6a45_icon-volunteer-1.avif",
            alt: "Voluntary",
          },
        },
        {
          value: "other",
          labelHtml: "Other",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69fa62f67e70f42de93f514e_other_icon_30px_antialiased.png",
            alt: "Other",
          },
        },
      ],
      rules: [
        {
          whenIncludesAnyOf: ["childCustody"],
          nextId: "qB3_custody_storyIntro",
        },
        {
          whenIncludesAnyOf: [
            "employment",
            "marriageRelationship",
            "voluntaryAccountability",
            "other",
          ],
          nextId: "qB3_share_storyIntro",
        },
      ],
      // defaultNextId: "qB2_incomplete_other",
    },

    qB3_custody_storyIntro: {
      id: "qB3_custody_storyIntro",
      type: "stories",
      headline: "We’ll tailor a plan that best fits your needs.",
      subheadlineHtml:
        "But first, <span class='u-bold'>take a look at some stories you might connect with.</span>",
      stories: [
        {
          id: "womanStory",
          title:
            "Choosing Support Over Stigma: Investing in Solutions That Work",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69b1d7bc6030135e0f4cc006_icon-play-blue.avif",
            alt: "play icon",
          },
          image: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69b9e825eea73494532e19a5_story-1.avif",
            alt: "Testimony thumbnail",
          },
          opensModalId: "womanStory",
        },
        {
          id: "manStory",
          title: "When Building Back Trust is in the Best Interest of the Kids",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69b1d7bc6030135e0f4cc006_icon-play-blue.avif",
            alt: "play icon",
          },
          image: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69b9e8254f0a53613fcbe744_story-2.avif",
            alt: "Testimony thumbnail",
          },
          opensModalId: "manStory",
        },
      ],
      primaryCta: {
        label: "Continue",
        nextId: "qB3a_monitoredClientIntro_receiver",
      },
    },
    qB3a_monitoredClientIntro_receiver: {
      id: "qB3a_monitoredClientIntro_receiver",
      type: "definition",
      headlineHtml: "<span style='color: #00abdf;'>Definition to Know</span>",
      textHtml:
        "The <span class='u-bold'>Monitored Client</span> is the person submitting Soberlink tests.",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8913bca74ea99f489308e_Level-1-Photo%201%20(1).avif",
      primaryCta: {
        label: "Continue",
        nextId: "qB4_monitoredClientFrequency",
      },
    },
    qB4_monitoredClientFrequency: {
      id: "qB4_monitoredClientFrequency",
      type: "singleChoice",
      text: "With your <span class='u-bold'>Monitored Client,</span> which option most fits your situation?",
      options: [
        {
          value: "everyDay",
          labelHtml:
            "<span class='u-normal'>Your</span> Monitored Client<span class='u-normal'> needs to</span> test every day.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f10cf15960ad2f62cb4_daily%20testing.avif",
            alt: "calendar with all days highlighted icon",
          },
          nextId: "qB4b_level2_intro_receiver",
        },
        {
          value: "parentingDaysOnly",
          labelHtml:
            "<span class='u-normal'>Your</span> Monitored Client<span class='u-normal'> only needs to</span> test on parenting days.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f106563beec4dbc11d9_icon-parenting-only-testing%201.avif",
            alt: "calendar icon with only several days highlighted",
          },
          nextId: "qB4b_level1_intro_receiver",
        },
      ],
    },
    qB4b_level2_intro_receiver: {
      id: "qB4b_level2_intro_receiver",
      type: "info",
      headlineHtml:
        "<span style='font-size: 20px;'>Because your <span class='u-bold'>Monitored Client needs to test everyday,</span> we suggest our:</span><br/><br/><span style='color: #00abdf;'>Level 2 - Daily Testing Program</span>",
      textHtml:
        "<span style='font-size: 16px;'>Consistent monitoring, 7 days a week. Testing schedules managed by Soberlink.</span>",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69b09a0c54e30e7580833743_level-2.avif",
      primaryCta: {
        label: "Next",
        nextId: "qB6_level2_shareScope_receiver",
      },
    },

    qB6_level2_shareScope_receiver: {
      id: "qB6_level2_shareScope_receiver",
      type: "singleChoice",
      introText:
        "To keep everyone informed, the results must be shared with a “Concerned Party.”",
      infoIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a9fcbcf5cd846f8b7e504b_icon%20info.png",
        alt: "Info icon",
        text: "What is a Concerned Party?",
      },
      infoLink: {
        type: "lightbox",
        id: "concernedPartyInfo",
        labelHtml: "Concerned Party info",
      },
      options: [
        {
          value: "onlyMe",
          labelHtml:
            "<span class='u-normal'>The</span> results only  <span class='u-normal'>need to be</span> shared with me, <span class='u-normal'>the Concerned Party.</span>",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd4bad2f8d698ab385_One%20Person.png",
            alt: "one person",
          },
          nextId: "qB7_level2_notify_onlyMe_receiver",
        },
        {
          value: "meAndOthers",
          labelHtml:
            "<span class='u-normal'>The</span> results <span class='u-normal'>need to be</span> shared with me and <span class='u-normal'>other</span> Contacts.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd9b14c609f0ac6f6f_Two%20People%20%2B.png",
            alt: "two people",
          },
          nextId: "qB7_level2_notify_meAndOthers_receiver",
        },
      ],
    },
    qB7_level2_notify_onlyMe_receiver: {
      id: "qB7_level2_notify_onlyMe_receiver",
      type: "singleChoice",
      text: "How should we send you the results?",
      choiceLayout: "planCards",
      size: "xlg",
      options: [
        {
          value: "emailNextDay",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed the next day.",
          metaHtml:
            "<div style='color: #26BCD7; font-weight: bold;'>Basic Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "basic",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_level2_basic",
        },
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed in real time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "plus",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_level2_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed and texted in real time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "premium",
            cadence: "mo",
          },
          badge: {
            label: "INCLUDES 50% OFF EXPERT TESTIMONY",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_level2_premium",
        },
      ],
    },
    qB7_level2_notify_meAndOthers_receiver: {
      id: "qB7_level2_notify_meAndOthers_receiver",
      type: "singleChoice",
      text: "How should we send you the results?",
      choiceLayout: "planCards",
      size: "xlg",
      options: [
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed in real time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "plus",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_level2_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed and texted in real time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_2",
            tier: "premium",
            cadence: "mo",
          },
          badge: {
            label: "INCLUDES 50% OFF EXPERT TESTIMONY",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_level2_premium",
        },
      ],
    },
    qB4b_level1_intro_receiver: {
      id: "qB4b_level1_intro_receiver",
      type: "info",
      headlineHtml:
        "<span style='font-size: 20px;'>Because your <span class='u-bold'>Monitored Client only needs to test on parenting days,</span> we suggest our:</span><br/><br/><span style='color: #00abdf;'>Level 1 - Parenting Time Only Program.</span>",
      textHtml:
        "<span style='font-size: 16px;'>This plan allows you to test only on days that you need to show proof of sobriety.</span>",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8913be2c8175724ce3d4f_Level-1-Photo%201.avif",
      primaryCta: { label: "Next", nextId: "qB5L1_testingDays_receiver" },
    },
    qB5L1_testingDays_receiver: {
      id: "qB5L1_testingDays_receiver",
      type: "singleChoice",
      text: "Our Level 1 Program includes 20 days of testing each month.",
      options: [
        {
          value: "twentyEnough",
          labelHtml:
            "20 testing days per month is enough. <span class='u-normal'>Extra days are $15 each.</span>",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8be108f33f4d708defb0b_Icon-Calendar-20-Days.avif",
            alt: "calendar icon",
          },
          nextId: "qB6_shareScope_receiver",
        },
        {
          value: "needMoreThanTwenty",
          labelHtml:
            "The Monitored Client needs more than 20 testing days per month.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8be1088cb4c64a242b2bd_Icon-Calendar-20-Plus-Days.avif",
            alt: "calendar icon",
          },
          nextId: "res_plan_level1_premium",
        },
      ],
    },
    qB6_shareScope_receiver: {
      id: "qB6_shareScope_receiver",
      type: "singleChoice",
      introText:
        "To keep everyone informed, your results must be shared with a “Concerned Party”.",
      infoIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a9fcbcf5cd846f8b7e504b_icon%20info.png",
        alt: "Info icon",
        text: "What is a Concerned Party?",
      },
      infoLink: {
        type: "lightbox",
        id: "concernedPartyInfo",
        labelHtml: "Concerned Party info",
      },
      options: [
        {
          value: "onlyMe",
          labelHtml:
            "<span class='u-normal'>The</span> results only <span class='u-normal'>need to be</span> shared with me, <span class='u-normal'>the Concerned Party.</span>",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd4bad2f8d698ab385_One%20Person.png",
            alt: "one person",
          },
          nextId: "qB7_notify_onlyMe_receiver",
        },
        {
          value: "meAndOthers",
          labelHtml:
            "<span class='u-normal'>The</span> results <span class='u-normal'>need to be</span> shared with me and <span class='u-normal'>other</span> Contacts.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd9b14c609f0ac6f6f_Two%20People%20%2B.png",
            alt: "two people",
          },
          nextId: "qB7_notify_meAndOthers_receiver",
        },
      ],
    },
    qB7_notify_onlyMe_receiver: {
      id: "qB7_notify_onlyMe_receiver",
      type: "singleChoice",
      text: "How should we send you the results?",
      choiceLayout: "planCards",
      size: "xlg",
      options: [
        {
          value: "emailNextDay",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed the next day.",
          metaHtml:
            "<div style='color: #26BCD7; font-weight: bold;'>Basic Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "basic",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_level1_basic",
        },
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed in real time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "plus",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_level1_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed and texted in real time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "premium",
            cadence: "mo",
          },
          badge: {
            label: "UNLIMITED TESTING DAYS",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_level1_premium",
        },
      ],
    },
    qB7_notify_meAndOthers_receiver: {
      id: "qB7_notify_meAndOthers_receiver",
      type: "singleChoice",
      text: "How should we send you the results?",
      choiceLayout: "planCards",
      size: "xlg",
      options: [
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed in real time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "plus",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_level1_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed and texted in real time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div>",
          priceRef: {
            kind: "plan",
            program: "level_1",
            tier: "premium",
            cadence: "mo",
          },
          badge: {
            label: "UNLIMITED TESTING DAYS",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_level1_premium",
        },
      ],
    },
    qB3_share_storyIntro: {
      id: "qB3_share_storyIntro",
      type: "stories",
      headline: "We’ll tailor a plan that best fits your needs.",
      subheadlineHtml:
        "But first, <span class='u-bold'>take a look at a story you might connect with.</span>",
      stories: [
        {
          id: "maxAndCami",
          title: "Watch Max and Cami's Story",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69b1d7bc6030135e0f4cc006_icon-play-blue.avif",
            alt: "Story icon",
          },
          image: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69bade14b9084d6258be21ca_Max-Cami-Cover-Help-Me-Choose.avif",
            alt: "Testimony thumbnail",
          },
          opensModalId: "maxAndCami",
        },
      ],
      primaryCta: { label: "Continue", nextId: "qB4_share_scope_receiver" },
    },
    qB4_share_scope_receiver: {
      id: "qB4_share_scope_receiver",
      type: "singleChoice",
      textHtml: "Who would you like the results shared with?",
      infoIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a9fcbcf5cd846f8b7e504b_icon%20info.png",
        alt: "Info icon",
        text: "What is a Contact?",
      },
      infoLink: {
        type: "lightbox",
        id: "contactInfo",
        labelHtml: "Contact info",
      },
      options: [
        {
          value: "onlyMe",
          labelHtml:
            "<span class='u-normal'>The</span> results <span class='u-normal'>only need to be</span> shared with me.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd4bad2f8d698ab385_One%20Person.png",
            alt: "one person",
          },
          nextId: "qB5_share_notify_onlyMe_receiver",
        },
        {
          value: "meAndOthers",
          labelHtml:
            "<span class='u-normal'>The</span> results <span class='u-normal'>need to be</span> shared with me and other Contacts.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/698131dd9b14c609f0ac6f6f_Two%20People%20%2B.png",
            alt: "two people",
          },
          nextId: "qB5_share_notify_meAndOthers_receiver",
        },
      ],
    },
    qB5_share_notify_onlyMe_receiver: {
      id: "qB5_share_notify_onlyMe_receiver",
      type: "singleChoice",
      text: "How should we send you the results?",
      size: "xlg",
      choiceLayout: "planCards",
      options: [
        {
          value: "emailNextDay",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed to me the next day.",
          metaHtml:
            "<div style='color: #26BCD7; font-weight: bold;'>Basic Plan</div>",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "basic",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_share_basic",
        },
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed in real time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "plus",
            cadence: "mo",
          },
          badge: {
            label: "MOST POPULAR",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_share_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed and texted in real time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div> ",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "premium",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_share_premium",
        },
      ],
    },

    qB5_share_notify_meAndOthers_receiver: {
      id: "qB5_share_notify_meAndOthers_receiver",
      type: "singleChoice",
      text: "How should we send you the results?",
      choiceLayout: "planCards",
      size: "xlg",
      options: [
        {
          value: "emailRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed in real time.",
          metaHtml:
            "<div style='color: #00ABDF; font-weight: bold;'>Plus Plan</div>",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "plus",
            cadence: "mo",
          },
          badge: {
            label: "MOST POPULAR",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "star icon",
            },
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738d52755adb3bba618_icon-email-alert.avif",
            alt: "email",
          },
          nextId: "res_plan_share_plus",
        },
        {
          value: "emailTextRealtime",
          labelHtml:
            "<span class='u-normal'>I want the test results</span> emailed and texted in real time.",
          metaHtml:
            "<div style='color: #1C4A82; font-weight: bold;'>Premium Plan</div> ",
          priceRef: {
            kind: "plan",
            program: "share",
            tier: "premium",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273806f904e006eb6249_icon-email-text-alert.avif",
            alt: "email and phone",
          },
          nextId: "res_plan_share_premium",
        },
      ],
    },

    qD1_paymentPreference: {
      id: "qD1_paymentPreference",
      type: "singleChoice",
      text: "Which option do you prefer?",
      size: "xxlg",
      options: [
        {
          value: "rent",
          labelHtml:
            "<div style='margin-bottom: 5px;'>Rent the Device <span class='u-normal'>from</span> {PRICE}<span style='font-size: 13px;'>/mo</span></div> <ul class='u-normal' style='font-size: 14px;'><li>Low monthly payment</li><li>No upfront device costs</li><li>Requires a monitoring plan commitment</li></ul>",
          priceRef: { kind: "deviceMin", commitment: "rent 365" },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a74e856cfb277a88a9ea3f_rent.avif",
            alt: "rent icon",
          },
          nextId: "qD2_rent_monitorDuration",
        },
        {
          value: "own",
          labelHtml:
            "<div style='margin-bottom: 5px;'>Own the Device <span class='u-normal'>from</span> {PRICE}</div> <ul class='u-normal' style='font-size: 14px;'><li>One-time purchase</li><li>Higher upfront costs</li><li>No Minimum Plan Commitment Required</li></ul>",
          priceRef: { kind: "deviceMin", commitment: "buy" },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a0227385cfc2c08d4208674_icon-buy.avif",
            alt: "buy icon",
          },
          nextId: "qD2_own_chooseDevice",
        },
      ],
    },
    qD2_own_chooseDevice: {
      id: "qD2_own_chooseDevice",
      type: "singleChoice",
      text: "Select the device that works best for you.",
      choiceLayout: "buyDeviceCards",
      size: "xlg",
      options: [
        {
          value: "connect",
          title: "{CONNECT_FAMILY_LABEL}",
          subtitle: "No minimum monitoring commitment required",
          descriptionHtml: `Bluetooth device uses smartphone to transmit test results.<br><span style='color: #00abdf; font-size: 10px;'>Smartphone pairing required.</span>`,
          priceRef: { kind: "device", device: "connect", commitment: "buy" },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6887f2ec5c894c7fd201e4d4_connect-dec-tree-100px-w.avif",
            alt: "{CONNECT_FAMILY_LABEL}",
          },
          nextId: "res_final_own_connect",
        },
        {
          value: "cellular 2",
          title: "Cellular 2",
          subtitle: "No minimum monitoring commitment required",
          descriptionHtml: `
          All-in-one device uses cellular data to transmit test results.<br><span style='color: #00abdf; font-size: 10px;'>No smartphone pairing required.</span>`,
          priceRef: { kind: "device", device: "cellular 2", commitment: "buy" },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6887f2ecf01bc5160d57ba58_cellular-2-dec-tree-100px-w.avif",
            alt: "Cellular 2",
          },
          nextId: "res_final_own_cellular2",
        },
      ],
    },
    qD2_rent_monitorDuration: {
      id: "qD2_rent_monitorDuration",
      type: "singleChoice",
      text: "How long do you plan on using Soberlink? Pay less by monitoring longer.",
      choiceLayout: "rentDeviceCards",
      size: "xxlg",
      options: [
        {
          value: "oneYear",
          labelHtml:
            "<span class='u-normal'>I plan to monitor for at least</span> one year.",
          badge: {
            label: "EXPERTS SUGGEST AT LEAST 1 YEAR OF MONITORING",
            icon: {
              url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6994c2f22b9a7cc99fa25884_Star%20Badge.png",
              alt: "info",
            },
          },
          metaHtml:
            "<div style='font-size: 16px;'>{CONNECT_FAMILY_LABEL} Device</div>",
          smartphoneReq: "Smartphone bluetooth pairing required",
          subMetaHtml: "Requires a 365-Day Monitoring Commitment",
          priceRef: {
            kind: "device",
            device: "connect",
            commitment: "rent 365",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a0227385d60e5e580e45d8b_icon-one-year-v2.avif",
            alt: "1 year calendar icon",
          },
          nextId: "res_final_rent_connect_19_365",
        },
        {
          value: "fourMonths",
          labelHtml:
            "<span class='u-normal'>I plan to monitor for at least</span> 4 months.",
          metaHtml:
            "<div style='font-size: 16px;'>{CONNECT_FAMILY_LABEL} Device</div>",
          smartphoneReq: "Smartphone bluetooth pairing required",
          subMetaHtml: "Requires a 120-Day Monitoring Commitment",
          priceRef: {
            kind: "device",
            device: "connect",
            commitment: "rent 120",
            cadence: "mo",
          },
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022738f054f35424d22dad_icon-four-months.avif",
            alt: "4 month calendar icon",
          },
          nextId: "res_final_rent_connect_29_120",
        },
      ],
    },
    qB_devicePurchaser: {
      id: "qB_devicePurchaser",
      type: "singleChoice",
      text: "Who will be purchasing the Soberlink Device?",
      options: [
        {
          value: "receiverWillPurchase",
          labelHtml:
            "<span class='u-normal'>I will be purchasing</span> the Soberlink Device for my Monitored Client.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a022739046c59d760b45307_icon-i-pay.avif",
            alt: "Black and white icon of a hand inserting a rectangular card into a vertical slot device",
          },
          nextId: "qD1_paymentPreference",
        },
        {
          value: "monitoredClientWillPurchase",
          labelHtml:
            "<span class='u-normal'>The Monitored Client will be purchasing</span> the Soberlink Device.",
          icon: {
            url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6a02273865c204f8710b7a74_icon-mc-pays.avif",
            alt: "Icon of a hand holding a card next to a person symbol",
          },
          nextId: "res_final_plan_only_device_by_monitored_client",
        },
      ],
    },
  },
  planFooters: {
    submitter: {
      textHtml: `
        <div style="text-align: center; font-size: 24px;">
          Now, let’s select your device.
        </div>
      `,
      ctaLabel: "Next",
    },
    receiver: {
      textHtml: `
        <div style="text-align: left; font-size: 16px;">
          Your Monitored Client will be able to choose their Device, or you can purchase on their behalf.<br><br>
          <span class='u-bold'>Devices</span> start at 
          <span class='u-bold'>{RENT_START}<span style='font-size: 14px;'>/mo</span></span> 
          to rent <span class='u-bold'>or {BUY_START}</span> to buy.
        </div>
      `,
      textTokens: {
        RENT_START: { kind: "deviceMin", commitment: "rent 365" },
        BUY_START: { kind: "deviceMin", commitment: "buy" },
      },
      ctaLabel: "Next",
    },
  },
  results: {
    res_plan_level2_basic: {
      id: "res_plan_level2_basic",
      type: "plan",
      programKey: "level_2",
      planKey: "basic",
      programDisplay: "Level 2 Daily Testing",
      headlineHtml: "We’ve selected a plan for you:",
      program: "Level 2",
      plan: "Basic",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/5f88919e0edbe064d62be70d_FL-Resources-5-Level2%20copy.avif",
      programIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f10cf15960ad2f62cb4_daily%20testing.avif",
        alt: "Level 2",
      },
      planIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/684c60995dc1a8007b27e9a6_Icon-Plan-Basic.avif",
        alt: "Basic",
      },
      priceRef: {
        kind: "plan",
        program: "level_2",
        tier: "basic",
        cadence: "mo",
      },
      nextId: "postPlan_router",
    },
    res_plan_level2_plus: {
      id: "res_plan_level2_plus",
      type: "plan",
      programKey: "level_2",
      planKey: "plus",
      programDisplay: "Level 2 Daily Testing",
      headlineHtml: "We’ve selected a plan for you:",
      program: "Level 2",
      plan: "Plus",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/5f88919e0edbe064d62be70d_FL-Resources-5-Level2%20copy.avif",
      programIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f10cf15960ad2f62cb4_daily%20testing.avif",
        alt: "Level 2",
      },
      planIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6849d98a1658cd2a8a322523_2084acb108cdee46636c09513576294ea46cbf9c.avif",
        alt: "Plus",
      },
      priceRef: {
        kind: "plan",
        program: "level_2",
        tier: "plus",
        cadence: "mo",
      },
      nextId: "postPlan_router",
    },
    res_plan_level2_premium: {
      id: "res_plan_level2_premium",
      type: "plan",
      programKey: "level_2",
      planKey: "premium",
      programDisplay: "Level 2 Daily Testing",
      headlineHtml: "We’ve selected a plan for you:",
      program: "Level 2",
      plan: "Premium",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/5f88919e0edbe064d62be70d_FL-Resources-5-Level2%20copy.avif",
      programIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f10cf15960ad2f62cb4_daily%20testing.avif",
        alt: "Level 2",
      },
      planIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/684c6099560a81fb3eccf802_Icon-Plan-Premium.avif",
        alt: "Premium",
      },
      priceRef: {
        kind: "plan",
        program: "level_2",
        tier: "premium",
        cadence: "mo",
      },
      nextId: "postPlan_router",
    },

    res_plan_level1_basic: {
      id: "res_plan_level1_basic",
      type: "plan",
      programKey: "level_1",
      planKey: "basic",
      programDisplay: "Level 1 Parenting Time Only",
      headlineHtml: "We’ve selected a plan for you:",
      program: "Level 1",
      plan: "Basic",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8913be2c8175724ce3d4f_Level-1-Photo%201.avif",
      programIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f106563beec4dbc11d9_icon-parenting-only-testing%201.avif",
        alt: "Level 1",
      },
      planIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/684c60995dc1a8007b27e9a6_Icon-Plan-Basic.avif",
        alt: "Basic",
      },
      priceRef: {
        kind: "plan",
        program: "level_1",
        tier: "basic",
        cadence: "mo",
      },
      nextId: "postPlan_router",
    },
    res_plan_level1_plus: {
      id: "res_plan_level1_plus",
      type: "plan",
      programKey: "level_1",
      planKey: "plus",
      programDisplay: "Level 1 Parenting Time Only",
      headlineHtml: "We’ve selected a plan for you:",
      program: "Level 1",
      plan: "Plus",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8913be2c8175724ce3d4f_Level-1-Photo%201.avif",
      programIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f106563beec4dbc11d9_icon-parenting-only-testing%201.avif",
        alt: "Level 1",
      },
      planIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6849d98a1658cd2a8a322523_2084acb108cdee46636c09513576294ea46cbf9c.avif",
        alt: "Plus",
      },
      priceRef: {
        kind: "plan",
        program: "level_1",
        tier: "plus",
        cadence: "mo",
      },
      nextId: "postPlan_router",
    },
    res_plan_level1_premium: {
      id: "res_plan_level1_premium",
      type: "plan",
      programKey: "level_1",
      planKey: "premium",
      programDisplay: "Level 1 Parenting Time Only",
      headlineHtml: "We’ve selected a plan for you:",
      program: "Level 1",
      plan: "Premium",
      textHtml: "This plan has unlimited testing days.",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8913be2c8175724ce3d4f_Level-1-Photo%201.avif",
      programIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69810f106563beec4dbc11d9_icon-parenting-only-testing%201.avif",
        alt: "Level 1",
      },
      planIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/684c6099560a81fb3eccf802_Icon-Plan-Premium.avif",
        alt: "Premium",
      },
      priceRef: {
        kind: "plan",
        program: "level_1",
        tier: "premium",
        cadence: "mo",
      },
      nextId: "postPlan_router",
    },
    res_plan_share_basic: {
      id: "res_plan_share_basic",
      type: "plan",
      programKey: "share",
      planKey: "basic",
      programDisplay: "Share Program",
      headlineHtml: "We’ve selected a plan for you:",
      program: "Share",
      plan: "Basic",
      textHtml: "",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8be1104143954697ecea4_Share.avif",
      programIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/688aa70a4aa70c72401a1784_e52682597e69004a549b6d3dfc6173aa993dd71c.avif",
        alt: "Share",
      },
      planIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/684c60995dc1a8007b27e9a6_Icon-Plan-Basic.avif",
        alt: "Basic",
      },
      priceRef: {
        kind: "plan",
        program: "share",
        tier: "basic",
        cadence: "mo",
      },
      nextId: "postPlan_router",
    },
    res_plan_share_plus: {
      id: "res_plan_share_plus",
      type: "plan",
      programKey: "share",
      planKey: "plus",
      programDisplay: "Share Program",
      headlineHtml: "We’ve selected a plan for you:",
      program: "Share",
      plan: "Plus",
      textHtml: "",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8be1104143954697ecea4_Share.avif",
      programIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/688aa70a4aa70c72401a1784_e52682597e69004a549b6d3dfc6173aa993dd71c.avif",
        alt: "Share",
      },
      planIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6849d98a1658cd2a8a322523_2084acb108cdee46636c09513576294ea46cbf9c.avif",
        alt: "Plus",
      },
      priceRef: {
        kind: "plan",
        program: "share",
        tier: "plus",
        cadence: "mo",
      },
      nextId: "postPlan_router",
    },
    res_plan_share_premium: {
      id: "res_plan_share_premium",
      type: "plan",
      programKey: "share",
      planKey: "premium",
      programDisplay: "Share Program",
      headlineHtml: "We’ve selected a plan for you:",
      program: "Share",
      plan: "Premium",
      textHtml: "",
      imageUrl:
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69a8be1104143954697ecea4_Share.avif",
      programIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/688aa70a4aa70c72401a1784_e52682597e69004a549b6d3dfc6173aa993dd71c.avif",
        alt: "Share",
      },
      planIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/684c6099560a81fb3eccf802_Icon-Plan-Premium.avif",
        alt: "Premium",
      },
      priceRef: {
        kind: "plan",
        program: "share",
        tier: "premium",
        cadence: "mo",
      },
      nextId: "postPlan_router",
    },
    res_final_plan_only_device_by_monitored_client: {
      id: "res_final_plan_only_device_by_monitored_client",
      type: "final",
      programFromPlan: true,
      planFromPlan: true,
      device: "Monitored Client to Choose",
      pricing: null,
      deviceIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69b1d7bcc03ce6233af92e9f_Icon-Unchoosen-Device.avif",
        alt: "Unchosen Device",
      },
      nextId: null,
    },
    res_final_own_connect: {
      id: "res_final_own_connect",
      type: "final",
      programFromPlan: true,
      planFromPlan: true,
      device: "Connect",
      ownership: "own",
      pricing: {
        devicePriceRef: {
          kind: "device",
          device: "connect",
          commitment: "buy",
        },
        devicePricePrefix: "starting at ",
        devicePriceSuffix: " (one-time purchase)",
        commitment: "no minimum plan commitment required",
      },
      deviceIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6887f2ec5c894c7fd201e4d4_connect-dec-tree-100px-w.avif",
        alt: "Connect Device",
      },
      nextId: null,
    },
    res_final_own_cellular2: {
      id: "res_final_own_cellular2",
      type: "final",
      programFromPlan: true,
      planFromPlan: true,
      device: "Cellular 2",
      ownership: "own",
      pricing: {
        devicePriceRef: {
          kind: "device",
          device: "cellular 2",
          commitment: "buy",
        },
        devicePricePrefix: "starting at ",
        devicePriceSuffix: " (one-time purchase)",
        commitment: "no minimum plan commitment required",
      },

      deviceIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6887f2ecf01bc5160d57ba58_cellular-2-dec-tree-100px-w.avif",
        alt: "Cellular 2 Device",
      },
      nextId: null,
    },

    res_final_rent_connect_19_365: {
      id: "res_final_rent_connect_19_365",
      type: "final",
      programFromPlan: true,
      planFromPlan: true,
      device: "Connect",
      ownership: "rent",
      pricing: {
        monthlyRef: {
          kind: "device",
          device: "connect",
          commitment: "rent 365",
          cadence: "mo",
        },
        commitment: "365-day monitoring commitment",
      },
      // text:
      //   "Our Recommendation\n\n" +
      //   "Soberlink is the ultimate investment in safety and trust—because time with your kids is priceless.\n\n" +
      //   "LEVEL & PLAN (from your previous selection),\n" +
      //   "CONNECT + $19/mo.\n\n" +
      //   "Add to Cart »  |  Email Recommendations »",
      deviceIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6887f2ec5c894c7fd201e4d4_connect-dec-tree-100px-w.avif",
        alt: "Connect Device",
      },
      nextId: null,
    },

    res_final_rent_connect_29_120: {
      id: "res_final_rent_connect_29_120",
      type: "final",
      programFromPlan: true,
      planFromPlan: true,
      device: "Connect",
      ownership: "rent",
      pricing: {
        monthlyRef: {
          kind: "device",
          device: "connect",
          commitment: "rent 120",
          cadence: "mo",
        },
        commitment: "120-day monitoring commitment",
      },
      // text:
      //   "Our Recommendation\n\n" +
      //   "Soberlink is the ultimate investment in safety and trust—because time with your kids is priceless.\n\n" +
      //   "LEVEL & PLAN (from your previous selection),\n" +
      //   "CONNECT + $29/mo.\n\n" +
      //   "Add to Cart »  |  Email Recommendations »",
      deviceIcon: {
        url: "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/6887f2ec5c894c7fd201e4d4_connect-dec-tree-100px-w.avif",
        alt: "Connect Device",
      },
      nextId: null,
    },
  },
};
